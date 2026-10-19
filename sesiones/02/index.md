---
sesion: 2
titulo: Dale memoria a tu landing page
title: "Sesión 2 · Dale memoria a tu landing page"
video: https://youtu.be/y9ELxSq3WH0
fecha: 2026-10-15
---

[Inicio](../../) · [Sesión 1](../01/) · **Sesión 2** · [Agenda de hoy](agenda/)

# Sesión 2 · Dale memoria a tu landing page

Hoy se acaba copiar y pegar código en GitHub: conectas tu carpeta con tu repositorio y le pides a la IA que publique tus cambios. Después le agregas a tu página un formulario de contacto, y cada mensaje que te dejen queda guardado en una base de datos.

> ▶ **Video, parte 1 · GitHub automatizado con IA:** [Ver en YouTube](https://youtu.be/y9ELxSq3WH0). Cubre la Parte 1 de esta guía y cada paso tiene un enlace al minuto exacto.
>
> ▶ **Video, parte 2 · Firebase y el formulario:** próximamente.
>
> 📝 **Pad de la clase:** [pad.riseup.net/p/vibe-coding-sesion2-15oct](https://pad.riseup.net/p/vibe-coding-sesion2-15oct). Escribe tu nombre en cada victoria y marca tu estado.

## Contenido

1. [Antes de empezar](#antes)
2. [Las dos victorias de hoy](#victorias)
3. [Parte 1 · Tu carpeta conectada a GitHub](#parte-1)
   - [Paso 1. Clona tu repositorio y conecta tu cuenta](#paso-1)
   - [Paso 2. Mírala en vivo y haz un cambio pequeño](#paso-2)
   - [Paso 3. Súbelo a internet](#paso-3)
   - [Un libro a muchas manos](#libro)
   - [Un cambio más grande con el agente](#cambio-grande)
4. [Parte 2 · Tu página con memoria](#parte-2)
   - [Paso 4. Crea tu proyecto en Firebase](#paso-4)
   - [Paso 5. Crea tu base de datos y protégela](#paso-5)
   - [Paso 6. Conecta tu página con Firebase](#paso-6)
   - [Paso 7. Guarda los mensajes en Firebase](#paso-7)
   - [Paso 8. Agradece en pantalla](#paso-8)
   - [Paso 9. Publícalo](#paso-9)
5. [Parte 3 · ¿Qué es una base de datos?](#parte-3)
6. [Taller para la sesión 3](#taller)
7. [Problemas frecuentes](#problemas)
8. [Glosario](#glosario)

<a id="antes"></a>

## Antes de empezar

- [ ] Tu página de la sesión 1 publicada en `https://TU-USUARIO.github.io/hello-world`
- [ ] **Git** instalado. En Windows, sigue [este video](https://www.youtube.com/watch?v=X8vmbhgDdZg). En Mac, abre la Terminal y escribe `git --version`: si te ofrece instalar las herramientas, acepta.
- [ ] Una cuenta de Google, para entrar a Firebase
- [ ] Antigravity instalado

<a id="victorias"></a>

## Las dos victorias de hoy

[▶ 1:28](https://youtu.be/y9ELxSq3WH0?t=88)

1. **Victoria 1:** cambias algo en tu computador y aparece en tu página publicada, sin copiar y pegar.
2. **Victoria 2:** alguien escribe en tu formulario y el mensaje aparece guardado en tu base de datos.

Vamos de a una. Lo que no se explica hoy, funciona igual: **confía en la magia**.

En el [pad de la clase](https://pad.riseup.net/p/vibe-coding-sesion2-15oct) escribe tu nombre debajo de cada victoria y marca tu estado:

- ✅ **Hecho:** ya lo ves en tu pantalla.
- 🙋 **Duda:** te trabaste. Escribe en qué paso, así te ayudamos.

---

<a id="parte-1"></a>

## Parte 1 · Tu carpeta conectada a GitHub

En la sesión 1 copiabas el código y lo pegabas en GitHub. Hoy conectas tu carpeta con tu repositorio: cambias en tu computador y lo subes con un clic o con una frase.

<a id="paso-1"></a>

### Paso 1. Clona tu repositorio y conecta tu cuenta

[▶ 1:44](https://youtu.be/y9ELxSq3WH0?t=104)

*Clonar* es bajar una copia de tu repositorio a tu computador, que queda conectada con GitHub.

1. En GitHub, abre tu repositorio. Haz clic en el botón de color **Code** y copia el link que termina en `.git`.

   ![El botón Code en GitHub, con el link para clonar](img/01-boton-code.jpg)

2. En Antigravity, abre la vista de **Source Control** (el ícono de ramitas, en la barra de la izquierda) y haz clic en **Clone Repository**. Pega el link y presiona Enter.

   ![Clone Repository en Antigravity](img/02-clone-repository.jpg)

3. **Conecta tu cuenta de GitHub (solo la primera vez)** [▶ 2:23](https://youtu.be/y9ELxSq3WH0?t=143). Antigravity te pide permiso para entrar a GitHub:
   - Haz clic en **Allow**.
   - Aparece un código. Haz clic en **Copy & Continue to GitHub**: se abre el navegador.
   - Pega el código, haz clic en **Authorize** y listo.

   ![Antigravity pide permiso para entrar a GitHub](img/03-permitir-github.jpg)

   ![El código de una sola vez](img/04-codigo-una-vez.jpg)

   > Si GitHub te pide confirmar con un código que llega a tu correo, búscalo en tu bandeja y pégalo. Es una verificación de seguridad de GitHub, no de Antigravity.

4. Elige dónde guardarlo (por ejemplo, tu carpeta de documentos) y haz clic en **Open**.

> **Desde hoy trabajas en esta carpeta nueva**, no en la de la sesión 1. Esta es la que está conectada con GitHub.

<a id="paso-2"></a>

### Paso 2. Mírala en vivo y haz un cambio pequeño

[▶ 4:47](https://youtu.be/y9ELxSq3WH0?t=287)

Antes de cambiar nada, pon tu página a correr en tu computador con **Live Server**.

*Live Server* es una extensión que convierte tu carpeta en un pequeño servidor web, como el de GitHub Pages pero en tu computador. Así tu página carga completa, como en internet: el `index.html` **y también** tus estilos (`.css`), tu código (`.js`) y tus imágenes.

**a. Instálala (solo la primera vez).**

1. En Antigravity, abre la vista de **Extensions** (el ícono de cuadritos, en la barra de la izquierda).
2. Busca `Live Server` y elige la de **Ritwick Dey** (el logo morado). Haz clic en **Install**.

**b. Enciéndela** [▶ 5:42](https://youtu.be/y9ELxSq3WH0?t=342)

1. Abre `index.html`.
2. Haz clic en **Go Live**, abajo a la derecha, en la barra de abajo.
3. Se abre tu navegador en una dirección como `http://127.0.0.1:5500`. Esa es tu página corriendo en vivo, en tu computador.

![Tu página corriendo en Live Server](img/05-go-live.jpg)

> **¿Cómo sé si estoy en mi computador o en internet?** Mira la dirección: si empieza por números (`127.0.0.1`), es tu computador y solo la ves tú. Si dice `github.io`, es internet y la ve cualquiera.

**c. Haz el cambio.**

1. En `index.html`, busca el título de tu hero.
2. Cámbiale una palabra, o una letra. Algo pequeño: la idea es probar el camino, no rediseñar.
3. Guarda (`Cmd + S` en Mac, `Ctrl + S` en Windows) y mira la pestaña de Live Server: el cambio aparece solo.

Fíjate en la vista de **Source Control**: aparece tu archivo con una **M**, de *modificado*. Git ya sabe que algo cambió.

<a id="paso-3"></a>

### Paso 3. Súbelo a internet

[▶ 6:07](https://youtu.be/y9ELxSq3WH0?t=367)

1. En **Source Control**, haz clic en el botón de estrellitas ✨ que está junto al mensaje: la IA lee tu cambio y te propone un mensaje. Puedes dejarlo o escribir el tuyo en español, por ejemplo `Cambié una letra de mi página`.
2. Haz clic en **Commit**.

   ![El mensaje del commit y el botón Commit](img/06-mensaje-commit.jpg)

3. Haz clic en **Sync Changes**. Te avisa que va a enviar tus cambios: dale **OK**.

   ![Sync Changes manda tus cambios a GitHub](img/07-sync-produccion.jpg)

4. Revisa que llegó [▶ 8:32](https://youtu.be/y9ELxSq3WH0?t=512): en GitHub, abre tu repositorio y la pestaña **Actions**. Espera el ✅ verde. Abre tu página publicada y refresca.

   ![Actions con el despliegue terminado](img/08-actions.jpg)

> ✅ **Victoria 1.** Cambiaste algo en tu computador y está en internet. Ese es el ciclo de hoy en adelante: **cambias → commit → push → publicado**.
>
> 📝 Marca tu estado en el [pad](https://pad.riseup.net/p/vibe-coding-sesion2-15oct).

| Palabra | Es como... |
|---|---|
| **Clonar** | Bajar una copia de tu Drive que se mantiene sincronizada |
| **Commit** | La minuta, como en la sesión 1: qué cambió y cuándo |
| **Push** (Sync) | Mandar tus minutas del computador a GitHub |
| **Producción** | La versión publicada, la que ve todo el mundo |

<a id="libro"></a>

### Un libro a muchas manos

[▶ 7:16](https://youtu.be/y9ELxSq3WH0?t=436)

¿Para qué tanto commit? Piensa en *Cien años de soledad*. Gabriel García Márquez era el autor, pero su agente literaria, Carmen Balcells, y sus editores seguramente le metieron mano al texto. Esos cambios hoy no se ven: nadie sabe quién cambió qué, ni cuándo.

![Un libro escrito a muchas manos](img/09-libro-a-muchas-manos.jpg)

Hoy un escritor puede compartir su documento y darles **permiso** a otros para editarlo. Con el código pasa lo mismo, pero mejor: en GitHub cada cambio queda firmado. Varias personas, **o varios agentes de IA**, pueden trabajar en el mismo proyecto, y siempre sabes quién cambió qué.

![Un texto en Docs y un código en GitHub](img/10-docs-y-github.jpg)

Eso fue lo que hiciste en el paso 1: darle permiso a tu computador para enviar cambios a tu repositorio.

<a id="cambio-grande"></a>

### Un cambio más grande con el agente

[▶ 9:02](https://youtu.be/y9ELxSq3WH0?t=542)

Ya probaste el camino con un cambio mínimo. Ahora pídele al agente algo más visible. Por ejemplo:

```
Cambia el estilo de la página para que se vea tipo mañana, no tipo noche como está ahora.
Agrega un botón para cambiar entre modo mañana y modo noche, en la esquina superior derecha.
```

1. Mira el resultado en la pestaña de Live Server [▶ 9:37](https://youtu.be/y9ELxSq3WH0?t=578). Si algo no te gusta, pídeselo, uno o dos cambios a la vez:

```
Quiero que los títulos no tengan degradado: usa un azul oscuro.
En el toggle de modo mañana y modo noche, quita las palabras y deja solo el ícono.
```

2. **¿Cómo se llama eso que quiero cambiar?** [▶ 10:44](https://youtu.be/y9ELxSq3WH0?t=644) La IA te entiende mejor si usas el nombre de cada pieza. En [The Component Gallery](https://component.gallery) encuentras los nombres, con ejemplos: un *toggle* (o *switch*) es el interruptor de dos estados, un *carousel* es el carrusel, un *popover* es la cajita que aparece encima. Casi todos están en inglés.

   ![The Component Gallery: el toggle y sus nombres](img/11-galeria-componentes.jpg)

3. Cuando te guste, pídele al agente que lo publique [▶ 12:32](https://youtu.be/y9ELxSq3WH0?t=752):

```
Está bien, sube a producción. Producción es hacer un commit a GitHub para el despliegue automático.
```

   ![Pídele al agente que suba a producción](img/12-sube-a-produccion.jpg)

4. En **Actions**, espera el nuevo ✅ y refresca tu página publicada [▶ 13:23](https://youtu.be/y9ELxSq3WH0?t=803).

   ![El nuevo despliegue en Actions](img/13-sexto-build.jpg)

> **Dos caminos, el mismo resultado.** Puedes subir tus cambios con los botones de Source Control (paso 3) o pidiéndoselo al agente. Al principio usa los botones, para ver qué pasa. Después, deja que el agente haga el trabajo.

---


<a id="parte-2"></a>

## Parte 2 · Tu página con memoria

<a id="paso-4"></a>

### Paso 4. Crea tu proyecto en Firebase

[Firebase](https://firebase.google.com) es un servicio de Google que le da a tu página lo que no tiene sola: una base de datos, usuarios, archivos. Hoy usamos solo la base de datos.

1. Entra a [console.firebase.google.com](https://console.firebase.google.com) con tu cuenta de Google.
2. **Crear un proyecto** (o **Agregar proyecto**). Ponle el nombre de tu página, por ejemplo `mi-landing`.
3. Si pregunta por **Google Analytics** o **Gemini**, puedes desactivarlos: hoy no los necesitas.
4. Espera a que termine y haz clic en **Continuar**.

<a id="paso-5"></a>

### Paso 5. Crea tu base de datos y protégela

1. En el menú de la izquierda, abre **Bases de datos y almacenamiento** (en inglés, **Databases & Storage**) y elige **Firestore**. Si no lo ves, escribe `Firestore` en el buscador de arriba.
2. **Crear base de datos.** Si pregunta por la edición, elige **Standard**. Deja la ubicación que aparece.
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

> **En una frase:** cualquiera puede dejarte un mensaje, pero nadie puede leerlos, cambiarlos ni borrarlos desde tu página. Tú los ves en la consola de Firebase.

<a id="paso-6"></a>

### Paso 6. Conecta tu página con Firebase

Registras tu página en Firebase y, a cambio, te da un bloque de código con la dirección de tu base de datos.

1. Vuelve a la página principal del proyecto (**Descripción general**, arriba a la izquierda) y haz clic en el botón **Agregar app**.
2. Te pregunta qué tipo de app es. Elige el ícono **`</>`** (Web).
3. Ponle un apodo, por ejemplo `landing`. **No** marques Firebase Hosting (ya publicas con GitHub Pages). **Registrar app.**
4. Te pregunta cómo agregar Firebase: elige **Usar una etiqueta `<script>`** (no npm). Aparece un bloque de código que empieza con `<script type="module">`. Cópialo **todo** con el botón de copiar. Lo vas a pegar en el paso 7.

> **¿Esa `apiKey` es secreta?** No. Es la dirección de tu base de datos y está bien que sea pública. Lo que protege tus mensajes son las reglas del paso 5.

<a id="paso-7"></a>

### Paso 7. Guarda los mensajes en Firebase

Primero, que los datos lleguen a Firebase. Que se vea bonito va en el paso 8.

1. Pídele al agente:

```
Antes del footer, agrega una sección de contacto con un formulario: nombre, correo, mensaje y un botón "Enviar". Usa el mismo estilo del resto de la página.
Conéctalo con Firebase usando JavaScript puro (sin npm ni frameworks), en un archivo nuevo app.js, enlazado al final de index.html con <script type="module" src="app.js"></script>.
Usa este bloque de Firebase y agrega Firestore desde el mismo CDN y la misma versión:
[pega aquí el bloque que copiaste en el paso 6]
Cada envío se guarda en la colección "mensajes" con los campos nombre, correo, mensaje y fecha (con serverTimestamp). Exactamente esos nombres.
```

2. El agente va a crear `app.js` y a tocar `index.html`. Revisa y acepta. No hace falta entender el código: **confía en la magia**.
3. En la pestaña de Live Server, llena el formulario con tus datos y haz clic en **Enviar**.
4. Ahora consúltalo en Firebase:
   - En el menú de la izquierda, haz clic en **Bases de datos y almacenamiento** → **Firestore**.
   - En la pestaña **Datos** aparece la colección `mensajes`. Haz clic en ella.
   - Haz clic en el documento que aparece (tiene un nombre raro, como `aB3xK9...`). A la derecha ves tus campos: `nombre`, `correo`, `mensaje` y `fecha`.

> ✅ **Victoria 2.** Tu página tiene memoria: lo que alguien escribe queda guardado en tu base de datos.
>
> 📝 Marca tu estado en el [pad](https://pad.riseup.net/p/vibe-coding-sesion2-15oct).

Los nombres de la colección y de los campos tienen que ser **exactamente** esos: las reglas del paso 5 solo aceptan esos. Si no aparece nada, mira [Problemas frecuentes](#problemas).

> **¿Perdiste el bloque de Firebase?** Haz clic en el engranaje ⚙ junto a **Descripción general** → **Configuración del proyecto**. Baja hasta **Tus apps**, elige **CDN** y cópialo con el botón de copiar.

<a id="paso-8"></a>

### Paso 8. Agradece en pantalla

Los datos ya se guardan, pero quien escribe no se entera. Ahora le respondes en la página.

1. Pídele al agente:

```
Cuando el mensaje se guarde en Firebase, cambia el formulario por: "¡Gracias por escribirme, [nombre]! Te respondo pronto a tu correo [correo]."
Pon el nombre y el correo con textContent, no como HTML.
Mientras se guarda, desactiva el botón y muestra "Enviando...". Si falla, muestra "No se pudo enviar, intenta de nuevo".
```

2. En la pestaña de Live Server, envía otro mensaje. Debe aparecer el agradecimiento con tu nombre y tu correo.
3. En Firestore, refresca la colección `mensajes`: ahora hay **dos** documentos.

> **¿Y las reglas?** Siguen igual. El agradecimiento usa lo que la persona acaba de escribir en el formulario, no lo lee de la base de datos. Por eso tu página puede saludarla por su nombre sin que nadie pueda leer los mensajes de los demás.

<a id="paso-9"></a>

### Paso 9. Publícalo

1. Súbelo con los botones de Source Control, como en el [paso 3](#paso-3), o pídeselo al agente:

```
Sube a producción con el mensaje "Agregué formulario de contacto".
```

2. Cuando **Actions** tenga ✅, abre tu página publicada y envía un mensaje desde ahí.
3. Míralo llegar a Firestore.

🎉 Tu página ya no solo muestra: también escucha.

---

<a id="parte-3"></a>

## Parte 3 · ¿Qué es una base de datos?

Una base de datos es un lugar ordenado donde tu página guarda información para consultarla después. Piensa en una hoja de cálculo:

| En Firestore | En una hoja de cálculo | En tu página |
|---|---|---|
| **Colección** | Una hoja | `mensajes` |
| **Documento** | Una fila | Un mensaje que alguien te dejó |
| **Campo** | Una columna | `nombre`, `correo`, `mensaje`, `fecha` |

Y las **reglas** son quién puede hacer qué con esa hoja: en tu página, cualquiera puede agregar una fila, pero solo tú, desde la consola, puedes leerlas.

Sin base de datos, tu página es un cartel: todos ven lo mismo. Con base de datos, empieza a ser una herramienta: recuerda lo que la gente hace en ella.

---

<a id="taller"></a>

## 🛠 Taller para la sesión 3

1. **Dale estilo a tu sección de contacto.** Selecciónala y pídele al agente cambios pequeños, como en la sesión 1. Usa tus colores de Coolors.
2. **Reto: agrega un campo nuevo**, por ejemplo "¿Cómo te enteraste de mi proyecto?". Ojo: las reglas solo aceptan los cuatro campos de hoy. Vas a tener que agregar el nombre del campo nuevo a la lista de `hasOnly` en las reglas. Si el formulario deja de guardar, ya sabes dónde mirar.

Recuerda subir cada cambio con un commit.

---

<a id="problemas"></a>

## Problemas frecuentes

| Lo que pasa | Qué hacer |
|---|---|
| No aparece **Go Live** | Revisa que Live Server esté instalado y que tengas abierto un archivo `.html`. Si sigue sin salir, reinicia Antigravity. |
| La dirección empieza por `file://` | Abriste el archivo con doble clic. Ciérrala y usa **Go Live**: la dirección debe empezar por `http://127.0.0.1`. |
| No aparece **Clone Repository** | Revisa que Git esté instalado: en una terminal, `git --version`. Si no responde, instálalo y reinicia Antigravity. |
| El commit falla con *"Please tell me who you are"* | Git no sabe tu nombre. Pídele al agente que lo configure con tu nombre y correo de GitHub. |
| El push pide usuario y contraseña en la terminal | Usa los botones de **Source Control**: escribe el mensaje, **Commit** y después **Sync Changes**. Autoriza GitHub en el navegador. |
| *"Missing or insufficient permissions"* al enviar | Los nombres no coinciden con las reglas. Revisa que la colección sea `mensajes` y los campos `nombre`, `correo`, `mensaje` y `fecha`, sin tildes ni mayúsculas. |
| No pasa nada al enviar | Clic derecho → **Inspeccionar** → **Console**. Copia el error en rojo y pégaselo al agente. |
| Funciona en mi computador pero no en la página publicada | Faltó el push, o Actions no ha terminado. Revisa que el commit esté en GitHub. |

<a id="glosario"></a>

## Glosario

Los términos de la sesión 1 están en su [glosario](../01/#glosario).

| Término | Qué es |
|---|---|
| **Base de datos** | Un lugar ordenado donde tu página guarda información para consultarla después. |
| **Campo** | Un dato dentro de un documento. Como una columna: `nombre`, `correo`, `mensaje`, `fecha`. |
| **CDN** | Un servidor que entrega código listo para usar, sin instalar nada. De ahí sale Firebase en tu página. |
| **Clonar** | Bajar una copia de tu repositorio a tu computador, que queda conectada con GitHub. |
| **Colección** | Un grupo de documentos del mismo tipo. Como una hoja de cálculo. La tuya se llama `mensajes`. |
| **Consola de Firebase** | La página web donde administras tu proyecto y ves los mensajes guardados. |
| **Consola del navegador** | Clic derecho → Inspeccionar → Console. Ahí aparecen los errores de tu página, en rojo. |
| **Documento** | Un registro dentro de una colección. Como una fila: un mensaje que alguien te dejó. |
| **Firebase** | Un servicio de Google que le da a tu página una base de datos, usuarios y archivos. |
| **`firebaseConfig`** | La dirección de tu proyecto de Firebase. Puede ser pública: lo que protege tus datos son las reglas. |
| **Firestore** | La base de datos de Firebase que usamos hoy. |
| **Formulario** | Los campos donde alguien escribe y el botón para enviar. |
| **Git** | El programa que lleva el historial de tu proyecto en tu computador y lo sincroniza con GitHub. |
| **Live Server** | Extensión que pone tu página a correr en tu computador, con todos sus archivos, y la refresca cada vez que guardas. |
| **Push** | Mandar tus commits de tu computador a GitHub. |
| **Reglas de seguridad** | Quién puede hacer qué con tu base de datos. En la tuya: cualquiera puede dejar un mensaje, nadie puede leerlo desde la página. |
| **SDK** | Una caja de herramientas de código para hablar con un servicio, en este caso con Firebase. |
| **`serverTimestamp`** | La hora del servidor de Firebase. Así la fecha de cada mensaje no depende del reloj de quien lo envía. |
| **Source Control** | La vista de Antigravity (el ícono de ramitas) que muestra qué archivos cambiaron. **M** = modificado. |
| **Terminal** | La ventana donde se escriben comandos, como `git --version`. |

---

[↑ Volver al contenido](#contenido) · [← Volver al inicio](../../)
