---
sesion: 3
titulo: Tu base de datos, ahora con IA
title: "Sesión 3 · Tu base de datos, ahora con IA"
fecha: 2026-10-22
---

[Inicio](../../) · [Sesión 1](../01/) · [Sesión 2](../02/) · **Sesión 3**

# Sesión 3 · Tu base de datos, ahora con IA

Hoy tu página aprende a escuchar: le agregas un formulario de contacto y cada mensaje que te dejen queda guardado en una base de datos. Después conectas el agente de Antigravity a esa base de datos, para que te responda en español qué te escribieron.

> ▶ **Video:** próximamente.
>
> 📝 **Pad de la clase:** [pad.riseup.net/p/vibe-coding-sesion3-22oct](https://pad.riseup.net/p/vibe-coding-sesion3-22oct). Escribe tu nombre en cada check-in y marca tu estado.

## Contenido

1. [Antes de empezar](#antes)
2. [Las dos victorias de hoy](#victorias)
3. [Parte 1 · Tu página con memoria](#parte-1)
   - [Paso 1. Crea tu proyecto en Firebase](#paso-1)
   - [Paso 2. Crea tu base de datos y protégela](#paso-2)
   - [Paso 3. Conecta tu página con Firebase](#paso-3)
   - [Paso 4. Guarda los mensajes en Firebase](#paso-4)
   - [Paso 5. Agradece en pantalla](#paso-5)
   - [Paso 6. Publícalo](#paso-6)
4. [¿Qué es una base de datos?](#base-de-datos)
5. [Parte 2 · El agente lee tu base de datos](#parte-2)
   - [Paso 7. Conecta el agente con Firebase](#paso-7)
   - [Paso 8. Pregúntale a tus mensajes](#paso-8)
6. [Taller](#taller)
7. [Problemas frecuentes](#problemas)
8. [Glosario](#glosario)

<a id="antes"></a>

## Antes de empezar

- [ ] Tu carpeta conectada a GitHub y abierta en Antigravity, como en la [sesión 2](../02/#paso-1). Si no la tienes, clónala con el paso 1 de esa guía.
- [ ] **Live Server** instalado ([sesión 2, paso 2](../02/#paso-2)).
- [ ] Una cuenta de Google, para entrar a Firebase. Usa una cuenta personal de Gmail: las cuentas de universidad o de empresa a veces tienen Firebase bloqueado.
- [ ] **Node.js** instalado. No lo usas sino hasta el [paso 7](#paso-7), pero instálalo antes de la clase porque tarda. Descárgalo de [nodejs.org](https://nodejs.org) (la versión LTS) e instálalo con las opciones que trae.

<a id="victorias"></a>

## Las dos victorias de hoy

1. **Victoria 1:** alguien escribe en tu formulario y el mensaje aparece guardado en tu base de datos.
2. **Victoria 2:** le preguntas al agente "¿qué me escribieron hoy?" y te responde con tus mensajes.

Vamos de a una. Lo que no se explica hoy, funciona igual: **confía en la magia**.

En el [pad de la clase](https://pad.riseup.net/p/vibe-coding-sesion3-22oct) escribe tu nombre debajo de cada check-in y marca tu estado:

- ✅ **Hecho:** ya lo ves en tu pantalla.
- 🙋 **Duda:** te trabaste. Escribe en qué paso, así te ayudamos.

---

<a id="parte-1"></a>

## Parte 1 · Tu página con memoria

<a id="paso-1"></a>

### Paso 1. Crea tu proyecto en Firebase

[Firebase](https://firebase.google.com) es un servicio de Google que le da a tu página lo que no tiene sola: una base de datos, usuarios, archivos. Hoy usamos solo la base de datos.

1. Entra a [console.firebase.google.com](https://console.firebase.google.com) con tu cuenta de Google. Si es tu primera vez, acepta las condiciones de Firebase.
2. **Crear un proyecto** (o **Agregar proyecto**). Ponle el nombre de tu página, por ejemplo `mi-landing`. Debajo del nombre aparece el **ID del proyecto**: anótalo, lo vas a usar en el [paso 8](#paso-8).
3. Si pregunta por **Google Analytics** o **Gemini**, puedes desactivarlos: hoy no los necesitas.
4. Espera a que termine y haz clic en **Continuar**.

<a id="paso-2"></a>

### Paso 2. Crea tu base de datos y protégela

1. En el menú de la izquierda, abre **Bases de datos y almacenamiento** (en inglés, **Databases & Storage**) y elige **Firestore**. Si no lo ves, escribe `Firestore` en el buscador de arriba.
2. **Crear base de datos.** Si pregunta por la edición, elige **Standard**. Deja la ubicación que aparece: no se puede cambiar después y para esta página da igual.
3. Elige **Modo de producción** (no el de prueba) y crea.
4. Ve a la pestaña **Reglas**, borra lo que hay, pega esto y haz clic en **Publicar**:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /mensajes/{mensaje} {
      allow create: if request.resource.data.keys().hasOnly(['nombre', 'correo', 'mensaje', 'fecha'])
                    && request.resource.data.nombre is string
                    && request.resource.data.correo is string
                    && request.resource.data.mensaje is string
                    && request.resource.data.mensaje.size() <= 2000
                    && request.resource.data.fecha == request.time;
      allow read, update, delete: if false;
    }
  }
}
```

Listo si ves la pestaña **Datos** vacía y, en **Reglas**, el aviso de que se publicaron.

> **En una frase:** cualquiera puede dejarte un mensaje, pero nadie puede leerlos, cambiarlos ni borrarlos desde tu página. Tú los ves en la consola de Firebase y, en la Parte 2, el agente los lee con tu cuenta.

<a id="paso-3"></a>

### Paso 3. Conecta tu página con Firebase

Registras tu página en Firebase y, a cambio, te da un bloque de código con la dirección de tu base de datos.

1. Vuelve a la página principal del proyecto (**Descripción general**, arriba a la izquierda) y haz clic en el botón **Agregar app**, o en el ícono **`</>`** si ya lo ves en la página principal.
2. Te pregunta qué tipo de app es. Elige el ícono **`</>`** (Web).
3. Ponle un apodo, por ejemplo `landing`. **No** marques Firebase Hosting (ya publicas con GitHub Pages). **Registrar app.**
4. Te pregunta cómo agregar Firebase: elige **Usar una etiqueta `<script>`** (no npm). Aparece un bloque de código que empieza con `<script type="module">`. Cópialo **todo** con el botón de copiar. Lo vas a pegar en el paso 4. **No cierres esta pestaña** hasta terminar el paso 4; si se te pierde, mira [cómo recuperarlo](#perdiste-bloque).
5. Haz clic en **Continuar a la consola**.

> **¿Esa `apiKey` es secreta?** No. Es la dirección de tu base de datos y está bien que sea pública. Lo que protege tus mensajes son las reglas del paso 2.

<a id="paso-4"></a>

### Paso 4. Guarda los mensajes en Firebase

Primero, que los datos lleguen a Firebase. Que se vea bonito va en el paso 5.

1. Pídele al agente:

```
Antes del footer (o al final de la página, si no tienes), agrega una sección de contacto con un formulario: nombre, correo, mensaje y un botón "Enviar". Usa el mismo estilo del resto de la página.
Conéctalo con Firebase usando JavaScript puro (sin npm ni frameworks), en un archivo nuevo app.js, enlazado al final de index.html con <script type="module" src="app.js"></script>.
Usa este bloque de Firebase y agrega Firestore desde el mismo CDN y la misma versión:
[pega aquí el bloque que copiaste en el paso 3]
Cada envío se guarda en la colección "mensajes" con los campos nombre, correo, mensaje y fecha (con serverTimestamp). Exactamente esos nombres.
```

2. El agente va a crear `app.js` y a tocar `index.html`. Revisa y acepta. No hace falta entender el código: **confía en la magia**.
3. Enciende **Go Live** y, en la pestaña de Live Server, llena el formulario con tus datos y haz clic en **Enviar**.
4. Ahora consúltalo en Firebase:
   - En el menú de la izquierda, haz clic en **Bases de datos y almacenamiento** → **Firestore**.
   - En la pestaña **Datos** aparece la colección `mensajes`. Haz clic en ella. Si no la ves, refresca la página de Firebase.
   - Haz clic en el documento que aparece (tiene un nombre raro, como `aB3xK9...`). A la derecha ves tus campos: `nombre`, `correo`, `mensaje` y `fecha`.

> ✅ **Victoria 1.** Tu página tiene memoria: lo que alguien escribe queda guardado en tu base de datos.
>
> 📝 Marca tu estado en el [pad](https://pad.riseup.net/p/vibe-coding-sesion3-22oct).

Los nombres de la colección y de los campos tienen que ser **exactamente** esos: las reglas del paso 2 solo aceptan esos. Si no aparece nada, mira [Problemas frecuentes](#problemas).

<a id="perdiste-bloque"></a>

> **¿Perdiste el bloque de Firebase?** Haz clic en el engranaje ⚙ junto a **Descripción general** → **Configuración del proyecto**. Baja hasta **Tus apps**, elige **CDN** y cópialo con el botón de copiar.

<a id="paso-5"></a>

### Paso 5. Agradece en pantalla

Los datos ya se guardan, pero quien escribe no se entera. Ahora le respondes en la página.

> **¿Vas atrasado?** Salta al [paso 6](#paso-6): este lo puedes hacer después, en el taller.

1. Pídele al agente:

```
Cuando el mensaje se guarde en Firebase, cambia el formulario por: "¡Gracias por escribirme, [nombre]! Te respondo pronto a tu correo [correo]."
Pon el nombre y el correo con textContent, no como HTML.
Mientras se guarda, desactiva el botón y muestra "Enviando...". Si falla, muestra "No se pudo enviar, intenta de nuevo".
```

   La línea de `textContent` evita que alguien meta código en tu página escribiéndolo en el formulario.

2. En la pestaña de Live Server, envía otro mensaje. Debe aparecer el agradecimiento con tu nombre y tu correo.
3. En Firestore, refresca la colección `mensajes`: aparece el documento nuevo.

> **¿Y las reglas?** Siguen igual. El agradecimiento usa lo que la persona acaba de escribir en el formulario, no lo lee de la base de datos. Por eso tu página puede saludarla por su nombre sin que nadie pueda leer los mensajes de los demás.

<a id="paso-6"></a>

### Paso 6. Publícalo

1. Súbelo con los botones de Source Control, como en la [sesión 2](../02/#paso-3), o pídeselo al agente:

```
Sube a producción con el mensaje "Agregué formulario de contacto".
```

2. Cuando **Actions** tenga ✅, abre tu página publicada y **deja dos o tres mensajes distintos**: una pregunta, un saludo, un pedido. Refresca la página entre uno y otro. Son los que el agente va a leer en la Parte 2.
3. Míralos llegar a Firestore.

🎉 Tu página ya no solo muestra: también escucha.

---

<a id="base-de-datos"></a>

## ¿Qué es una base de datos?

Una base de datos es un lugar ordenado donde tu página guarda información para consultarla después. Piensa en una hoja de cálculo:

| En Firestore | En una hoja de cálculo | En tu página |
|---|---|---|
| **Colección** | Una hoja | `mensajes` |
| **Documento** | Una fila | Un mensaje que alguien te dejó |
| **Campo** | Una columna | `nombre`, `correo`, `mensaje`, `fecha` |

Y las **reglas** son quién puede hacer qué con esa hoja: en tu página, cualquiera puede agregar una fila, pero solo tú puedes leerlas.

Sin base de datos, tu página es un cartel: todos ven lo mismo. Con base de datos, empieza a ser una herramienta: recuerda lo que la gente hace en ella.

---

<a id="parte-2"></a>

## Parte 2 · El agente lee tu base de datos

Hasta ahora, para ver tus mensajes tenías que entrar a la consola de Firebase y abrirlos uno por uno. Ahora le das al agente de Antigravity acceso a tu base de datos, para que los lea por ti y te responda en español.

Eso se hace con **MCP**: un enchufe que le da al agente acceso a una herramienta, en este caso Firebase.

> **¿Por qué el agente sí puede leer y la página no?** Tu página es pública, por eso sus reglas solo dejan escribir. El agente entra con **tu** cuenta de Google, como cuando abres la consola de Firebase.

<a id="paso-7"></a>

### Paso 7. Conecta el agente con Firebase

> **¿No tienes Node.js?** Instálalo desde [nodejs.org](https://nodejs.org) (la versión LTS), reinicia Antigravity y sigue.

1. En Antigravity, abre el panel del agente. Haz clic en los tres puntos **⋯** de arriba → **MCP Servers**.
2. Busca **Firebase** en la lista y haz clic en **Install**.

   Si quieres ver qué quedó instalado: **Manage MCP Servers** → **View raw config**. Debe aparecer algo así:

```json
{
  "mcpServers": {
    "firebase-mcp-server": {
      "command": "npx",
      "args": ["-y", "firebase-tools@latest", "mcp"]
    }
  }
}
```

3. **Inicia sesión en Firebase (solo la primera vez).** Abre la terminal de Antigravity (menú **Terminal** → **New Terminal**), pega esto y presiona Enter:

```
npx -y firebase-tools@latest login
```

   Si te pregunta si quieres enviar datos de uso a Firebase, responde lo que prefieras. Se abre el navegador: elige **la misma cuenta** con la que creaste el proyecto y acepta. Cuando la terminal diga *Success*, ya está.

<a id="paso-8"></a>

### Paso 8. Pregúntale a tus mensajes

Pídele al agente, cambiando `mi-landing` por el ID de tu proyecto (el que anotaste en el paso 1):

```
Usa Firebase para leer la colección "mensajes" de mi proyecto mi-landing. ¿Qué me escribieron hoy? Resúmelo en una lista corta.
```

Prueba otras preguntas:

```
¿Alguien me pidió algo concreto? ¿Quién y qué?
```

```
¿Cuántos mensajes tengo y de cuántas personas distintas?
```

> ✅ **Victoria 2.** Ya no abres tus mensajes uno por uno: le preguntas al agente y te responde con lo que guardó tu página.
>
> 📝 Marca tu estado en el [pad](https://pad.riseup.net/p/vibe-coding-sesion3-22oct).

---

<a id="taller"></a>

## 🛠 Taller

1. **Dale estilo a tu sección de contacto.** Selecciónala y pídele al agente cambios pequeños, como en la sesión 1. Usa tus colores de Coolors.
2. **Pídele al agente un resumen semanal:** quién te escribió, qué te pidieron y a quién te falta responder.
3. **Reto: agrega un campo nuevo**, por ejemplo "¿Cómo te enteraste de mi proyecto?". Ojo: las reglas solo aceptan los cuatro campos de hoy. Vas a tener que agregar el nombre del campo nuevo a la lista de `hasOnly` en las reglas. Si el formulario deja de guardar, ya sabes dónde mirar.

Recuerda subir cada cambio con un commit.

---

<a id="problemas"></a>

## Problemas frecuentes

| Lo que pasa | Qué hacer |
|---|---|
| *"Missing or insufficient permissions"* al enviar | Los nombres no coinciden con las reglas. Revisa que la colección sea `mensajes` y los campos `nombre`, `correo`, `mensaje` y `fecha`, sin tildes ni mayúsculas. |
| No pasa nada al enviar | Clic derecho → **Inspeccionar** → **Console**. Copia el error en rojo y pégaselo al agente. |
| La dirección empieza por `file://` | Abriste el archivo con doble clic. Ciérrala y usa **Go Live**: la dirección debe empezar por `http://127.0.0.1`. |
| Funciona en mi computador pero no en la página publicada | Faltó el push, o Actions no ha terminado. Revisa que el commit esté en GitHub. |
| El agente dice que no encuentra `npx` | Falta Node.js. Instálalo desde [nodejs.org](https://nodejs.org) y reinicia Antigravity. |
| El agente no ve tu proyecto | Iniciaste sesión con otra cuenta de Google. En la terminal: `npx -y firebase-tools@latest logout` y después `login` con la cuenta del proyecto. |

<a id="glosario"></a>

## Glosario

Los términos de las sesiones anteriores están en los glosarios de la [sesión 1](../01/#glosario) y la [sesión 2](../02/#glosario).

| Término | Qué es |
|---|---|
| **Base de datos** | Un lugar ordenado donde tu página guarda información para consultarla después. |
| **Campo** | Un dato dentro de un documento. Como una columna: `nombre`, `correo`, `mensaje`, `fecha`. |
| **CDN** | Un servidor que entrega código listo para usar, sin instalar nada. De ahí sale Firebase en tu página. |
| **Colección** | Un grupo de documentos del mismo tipo. Como una hoja de cálculo. La tuya se llama `mensajes`. |
| **Consola de Firebase** | La página web donde administras tu proyecto y ves los mensajes guardados. |
| **Consola del navegador** | Clic derecho → Inspeccionar → Console. Ahí aparecen los errores de tu página, en rojo. |
| **Documento** | Un registro dentro de una colección. Como una fila: un mensaje que alguien te dejó. |
| **Firebase** | Un servicio de Google que le da a tu página una base de datos, usuarios y archivos. |
| **`firebaseConfig`** | La dirección de tu proyecto de Firebase. Puede ser pública: lo que protege tus datos son las reglas. |
| **Firestore** | La base de datos de Firebase que usamos hoy. |
| **Formulario** | Los campos donde alguien escribe y el botón para enviar. |
| **MCP** | Un enchufe que le da al agente acceso a una herramienta externa, como tu base de datos. |
| **Node.js** | Un programa que deja correr herramientas de JavaScript en tu computador. Lo necesita el enchufe de Firebase. |
| **Reglas de seguridad** | Quién puede hacer qué con tu base de datos. En la tuya: cualquiera puede dejar un mensaje, nadie puede leerlo desde la página. |
| **SDK** | Una caja de herramientas de código para hablar con un servicio, en este caso con Firebase. |
| **`serverTimestamp`** | La hora del servidor de Firebase. Así la fecha de cada mensaje no depende del reloj de quien lo envía. |

---

[↑ Volver al contenido](#contenido) · [← Volver al inicio](../../)
