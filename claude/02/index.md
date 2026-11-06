---
ciclo: claude
sesion: 2
titulo: Construye como profesional
serie: Sesiones con Claudio
title: "Sesiones con Claudio · Sesión 2 · Construye como profesional"
fecha: 2026-11-05
---

[Inicio](../../) · **Sesiones con Claudio · Sesión 2**

# Sesión 2 · Construye como profesional

En la sesión 1 construiste tu app con Claude Code. Hoy trabajas como lo hace un profesional: le das
a Claudio una **memoria** que no se olvida, le enseñas a **diseñar** con una skill, le pides una
**revisión** con ojos frescos y **publicas** tu app con un enlace. Cuatro pasos:
**memoria → diseño → revisión → publicar**.

> ▶ **Video:** próximamente.
>
> 📝 **Pad de la clase:** PENDIENTE (enlace del pad del 5 de noviembre). Escribe tu nombre en cada check-in y marca tu estado.

## Contenido

1. [Antes de empezar](#antes)
2. [Las cuatro victorias de hoy](#victorias)
3. [El dato: el 98 % es releer](#dato)
4. [Paso 0. ¿Traes tu app?](#paso-0)
5. [Parte 1 · Memoria](#parte-1)
   - [Paso 1. Crea la memoria con /init](#paso-1)
   - [Paso 2. Cuida la mesa](#paso-2)
6. [Parte 2 · Diseño con Hallmark](#parte-2)
   - [Qué es una skill](#skill)
   - [Paso 3. Instala Hallmark](#paso-3)
   - [Paso 4. Rediseña tu app](#paso-4)
7. [Parte 3 · Revisa y publica](#parte-3)
   - [Paso 5. Revisión con un subagente y commit](#paso-5)
   - [Paso 6. Publica con GitHub Pages](#paso-6)
8. [Taller](#taller)
9. [Próximo jueves](#proximo)
10. [Glosario](#glosario)

<a id="antes"></a>

## Antes de empezar

- [ ] **Claude Code instalado** y tu cuenta de Claude Pro (o Max). Si no lo tienes, sigue los pasos 1 y 2 de la [sesión 1](../01/#paso-1).
- [ ] **Tu app de la sesión 1** (o la del taller). ¿No tienes? Mira el [paso 0](#paso-0).
- [ ] **Node 18 o más**, para instalar Hallmark. Compruébalo en la terminal con `node -v`.
- [ ] **GitHub CLI (`gh`)** con tu sesión iniciada. Si no lo hiciste, sigue el [paso 11 de la sesión 1](../01/#paso-11).

<a id="victorias"></a>

## Las cuatro victorias de hoy

1. **Victoria 1:** cierras Claude Code, lo abres otra vez y se acuerda de tu app.
2. **Victoria 2:** escribes `/` y aparece `hallmark`.
3. **Victoria 3:** el antes y el después de tu app, rediseñada.
4. **Victoria 4:** tu app tiene enlace.

En el pad de la clase escribe tu nombre debajo de cada check-in y marca tu estado:

- ✅ **Hecho:** ya lo ves en tu pantalla.
- 🙋 **Duda:** te trabaste. Escribe en qué paso, así te ayudamos.

<a id="dato"></a>

## El dato: el 98 % es releer

El profe midió los tokens que gastó Claudio editando los videos del Nivelatorio. **Entre el 97 % y
el 99 % fue Claudio releyendo la conversación.** Dos ideas salen de ahí:

1. **En cada mensaje, Claudio vuelve a leer toda la mesa.** Lo que dejas encima lo pagas una y otra vez.
2. **Lo que no está en la mesa, no se paga.**

La meta de hoy: que Claudio gaste menos y recuerde más.

<a id="paso-0"></a>

## Paso 0. ¿Traes tu app?

**Sí:** abre la terminal en la carpeta de tu app y escribe:

```
claude
```

**¿Sin app?** Baja la del profe, la de las cuentas del viaje familiar:

```
git clone https://github.com/juandaveth-profe/cuentas-viaje.git
cd cuentas-viaje
claude
```

Nadie se queda sin app.

<a id="parte-1"></a>

## Parte 1 · Memoria

Cada vez que abres Claude Code, Claudio arranca sin acordarse de nada: no sabe qué es tu app ni qué
decidieron juntos. Para eso existe `CLAUDE.md`, un archivo en tu carpeta que Claudio lee al empezar.

<a id="paso-1"></a>

### Paso 1. Crea la memoria con /init

Dentro de Claude Code, escribe:

```
/init
```

Claudio lee tu proyecto y escribe su memoria en `CLAUDE.md`. Ábrelo y léelo. Tres reglas para
cuidarlo:

1. **Corto.** Se carga en cada mensaje, así que cada línea cuesta.
2. **Lo que Claudio repite mal, va aquí.** Si le corriges lo mismo dos veces, escríbelo en `CLAUDE.md`.
3. **Cómo se prueba tu app.** Tu criterio de éxito (por ejemplo, el caso de la cena de 90.000 entre tres) para que Claudio sepa verificar.

Ahora sal con `/exit`, vuelve a abrir con `claude` y pregúntale qué hace tu app.

✅ **Victoria 1** cuando cierres, abras y Claudio se acuerde de tu app sin explicarle.

<a id="paso-2"></a>

### Paso 2. Cuida la mesa

Tres comandos para que la mesa no se llene de lo que no necesitas:

1. **Mira:** `/context` antes y después del `CLAUDE.md`. ¿Cuánto ocupa la memoria?
2. **Limpia:** `/clear` entre tareas. Una tarea, una sesión.
3. **Resume:** cuando la conversación ya es larga y no quieres empezar de cero, dile qué guardar:

```
/compact conserva las decisiones de diseño
```

<a id="parte-2"></a>

## Parte 2 · Diseño con Hallmark

<a id="skill"></a>

### Qué es una skill

Una **skill** es un manual en el cajón.

| | Dónde está | Qué ocupa en la mesa |
|---|---|---|
| **`CLAUDE.md`** | Siempre en la mesa | Todo: se lee en cada mensaje |
| **Skill** | En el cajón | Solo el nombre y la descripción, hasta que Claudio la abre |

Claudio abre la skill cuando la necesita. Por eso puedes tener muchas y casi no ocupan. Hoy
instalamos una; en la sesión 3 haces la tuya.

<a id="paso-3"></a>

### Paso 3. Instala Hallmark

**Hallmark** es una skill de diseño para que tu app no se vea hecha por IA. Es abierta (licencia
MIT) y la hizo Together AI. Pide Node 18 o más.

En la terminal (fuera de Claude Code):

```
node -v
npx skills add nutlope/hallmark -g --agent claude-code
claude
```

Dentro de Claude Code, escribe `/` y busca `hallmark` en la lista.

✅ **Victoria 2** cuando escribas `/` y aparezca `hallmark`.

<a id="paso-4"></a>

### Paso 4. Rediseña tu app

Primero el plan, después el diseño. Presiona **Shift+Tab** hasta el **modo plan** y escribe:

```
/hallmark redesign index.html
```

Hay que llamarla por su nombre: sin eso, Hallmark no toca un diseño que ya existe.

Lee el plan que te propone. Si te convence, apruébalo con **auto-aceptar** y mira cómo trabaja.
Antes de empezar, toma una captura de tu app para comparar.

¿Se ve hecha por una persona?

✅ **Victoria 3** cuando tengas el antes y el después.

<a id="parte-3"></a>

## Parte 3 · Revisa y publica

<a id="paso-5"></a>

### Paso 5. Revisión con un subagente y commit

Un **subagente** es otro Claudio que trabaja en su propia mesa: lee lo que necesite y solo te
devuelve el resumen. Así tu mesa no se llena con la revisión. Pega este prompt:

> Usa un subagente para revisar mis cambios con ojos frescos

Si la revisión sale bien, pídele el commit.

<a id="paso-6"></a>

### Paso 6. Publica con GitHub Pages

**GitHub Pages** publica tu app gratis con un enlace público. Si todavía no iniciaste sesión en
GitHub desde la terminal, hazlo una sola vez (lo haces tú, no Claudio):

```
! gh auth login
```

Las respuestas están en el [paso 11 de la sesión 1](../01/#paso-11). Después pega este prompt:

> Súbela a GitHub y actívale GitHub Pages

Si tu app todavía no tiene repositorio, Claudio puede proponerte algo como:

```
gh repo create cuentas-viaje --public --source=. --push
```

Cambia `cuentas-viaje` por el nombre de tu app. Para publicar con GitHub Pages gratis, el
repositorio tiene que ser público: antes de aprobar, revisa que no haya datos que no quieras mostrar.

✅ **Victoria 4** cuando tu app tenga enlace. Compártelo en el pad.

<a id="taller"></a>

## Taller

1. Agrega a `CLAUDE.md` algo que Claudio repite mal.
2. Pásale una auditoría de diseño a tu app:
   ```
   /hallmark audit index.html
   ```
3. Comparte tu enlace en la comunidad.

<a id="proximo"></a>

## Próximo jueves

**Sesión 3 · Hazla tuya.** Haces tu propia skill y le conectas herramientas a Claudio: MCP y hooks.

Aquí no hay preguntas bobas.

<a id="glosario"></a>

## Glosario

- **`CLAUDE.md`:** la memoria de tu proyecto. Claudio la lee al empezar cada sesión.
- **`/init`:** el comando que le pide a Claudio leer tu proyecto y escribir su `CLAUDE.md`.
- **`/context`:** muestra qué tan llena está la mesa (ventana de contexto).
- **`/clear`:** limpia la mesa para empezar una tarea nueva.
- **`/compact`:** resume la conversación para hacer espacio; le puedes decir qué conservar.
- **Skill:** un manual que Claudio guarda en el cajón y abre solo cuando lo necesita.
- **Hallmark:** una skill de diseño para que tu app no se vea hecha por IA.
- **Subagente:** otro Claudio que trabaja en su propia mesa y te devuelve solo el resumen.
- **GitHub Pages:** el servicio de GitHub que publica gratis una página desde tu repositorio.

---

[Inicio](../../)
