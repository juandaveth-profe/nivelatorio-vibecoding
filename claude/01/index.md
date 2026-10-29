---
ciclo: claude
sesion: 1
titulo: Desarma una app. Construye la tuya.
serie: Sesiones con Claudio
title: "Sesiones con Claudio · Sesión 1 · Desarma una app. Construye la tuya."
fecha: 2026-10-29
---

[Inicio](../../) · **Sesiones con Claudio · Sesión 1**

# Sesión 1 · Desarma una app. Construye la tuya.

Hoy aprendes a trabajar con **Claude Code**, el agente de Claude que vive en tu terminal. Primero
desarmamos una app real de dividir gastos para entender cómo está hecha, y después construimos la
nuestra. Todo con un mismo método de cuatro pasos: **explorar → planear → codificar → commit**.

> 🤖 **¿Por qué "Claudio"?** Así le decimos de cariño a Claude en esta serie de tres sesiones.
> Cuando leas *Claudio*, hablamos de Claude. Ojo: en la terminal, en los comandos y en la app se
> sigue escribiendo `claude`.

> ▶ **Video:** próximamente.
>
> 📝 **Pad de la clase:** [pad.riseup.net/p/vibe-coding-sesiones-con-claudio-29-oct](https://pad.riseup.net/p/vibe-coding-sesiones-con-claudio-29-oct). Escribe tu nombre en cada check-in y marca tu estado.

## Contenido

1. [Antes de empezar](#antes)
2. [Las cuatro victorias de hoy](#victorias)
3. [Qué es Claude Code](#que-es)
4. [Parte 0 · Instala Claude Code](#parte-0)
   - [Paso 1. Instálalo desde la terminal](#paso-1)
   - [Paso 2. Primer arranque](#paso-2)
   - [Paso 3. Los modos de permiso](#paso-3)
5. [Parte 1 · Explorar: desarma Spliit](#parte-1)
   - [Paso 4. Conecta REA](#paso-4)
   - [Paso 5. Pregúntale a Spliit cómo funciona](#paso-5)
6. [La mesa de trabajo (ventana de contexto)](#mesa)
7. [Parte 2 · Planear](#parte-2)
   - [Paso 6. Una carpeta nueva para tu app](#paso-6)
   - [Paso 7. Pídele un plan](#paso-7)
8. [Parte 3 · Codificar](#parte-3)
   - [Paso 8. Aprueba el plan y pruébala](#paso-8)
9. [Parte 4 · Commit](#parte-4)
   - [Paso 9. Revisión y commit](#paso-9)
10. [Taller](#taller)
11. [Problemas frecuentes](#problemas)
12. [Glosario](#glosario)

<a id="antes"></a>

## Antes de empezar

- [ ] **Una cuenta de Claude Pro** (o Max). Con el plan gratis, Claude Code no funciona. ¿No tienes Pro? Mira la [nota de la Claude Console](#sin-pro).
- [ ] **Node.js**, la versión LTS de [nodejs.org](https://nodejs.org). Instálala aunque ya tengas Node: REA pide una versión reciente.
- [ ] **Git.** En Mac ya viene (si al usarlo te pide instalar las herramientas de desarrollo, acepta). En Windows, instala [Git for Windows](https://git-scm.com/downloads/win) con las opciones que trae.
- [ ] Si puedes, instala Claude Code antes de la clase con el [paso 1](#paso-1).

<a id="victorias"></a>

## Las cuatro victorias de hoy

1. **Victoria 1:** Claude Code y REA conectados.
2. **Victoria 2:** Claude te explica cómo Spliit calcula quién le debe a quién.
3. **Victoria 3:** registras un gasto en tu app y te dice quién debe cuánto.
4. **Victoria 4:** tu primer commit, hecho con Claude, aparece en `git log`.

Vamos de a una. Lo que no se explica hoy, funciona igual: **confía en la magia**.

En el [pad de la clase](https://pad.riseup.net/p/vibe-coding-sesiones-con-claudio-29-oct) escribe tu nombre debajo de cada check-in y marca tu estado:

- ✅ **Hecho:** ya lo ves en tu pantalla.
- 🙋 **Duda:** te trabaste. Escribe en qué paso, así te ayudamos.

<a id="que-es"></a>

## Qué es Claude Code

Claude Code es un **agente**: un asistente que no solo te responde, sino que actúa. Usa
herramientas, mira el resultado y vuelve a intentar hasta lograr lo que le pediste. Funciona en un
ciclo: tú le pides algo, reúne el contexto que necesita, actúa, verifica, y si no quedó bien, vuelve
a empezar. Lo puedes interrumpir en cualquier momento con **Esc**.

Con Claude Code puedes:

- **Leer y entender un proyecto:** que te explique cómo funciona algo o dónde está un error.
- **Editar archivos:** crear y cambiar los archivos de tu carpeta.
- **Correr comandos:** instalar cosas, ejecutar herramientas y decidir qué hacer con lo que respondan.
- **Buscar en la web:** documentación o la versión más nueva de una herramienta.

**¿En qué se diferencia de lo que ya conoces?**

| | Chat de Claude | Antigravity | Claude Code |
|---|---|---|---|
| Qué es | Un chat | Un editor de código con agentes | Un agente en la terminal |
| Qué ve | Lo que le pegas o subes | La carpeta abierta | La carpeta donde lo abres |
| Ves el código | Solo el que te muestra | Siempre, en el editor | Solo los cambios que hace |
| Mejor para | Pensar y preguntar | Ver el código mientras el agente trabaja | Delegarle tareas enteras |

Antigravity es como tener al agente sentado a tu lado. Con Claude Code, le das la llave de tu
carpeta y te va mostrando lo que hace. Claude Code también existe como extensión de VS Code, como
app de escritorio y en la web; en este ciclo lo usamos en la terminal.

<a id="parte-0"></a>

## Parte 0 · Instala Claude Code

<a id="paso-1"></a>

### Paso 1. Instálalo desde la terminal

Abre la terminal de tu sistema, pega el comando y presiona Enter. El instalador no muestra avance
mientras descarga: espera a que termine.

| | Cómo abrir la terminal | Comando |
|---|---|---|
| **Mac** | Cmd+Espacio, escribe "Terminal" | `curl -fsSL https://claude.ai/install.sh \| bash` |
| **Linux** | Ctrl+Alt+T (Ubuntu) | `curl -fsSL https://claude.ai/install.sh \| bash` |
| **Windows** | Tecla Windows, escribe "PowerShell" | `irm https://claude.ai/install.ps1 \| iex` |

En Windows también puedes usar CMD:
`curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd`

<a id="paso-2"></a>

### Paso 2. Primer arranque

1. **Cierra la terminal y abre una nueva.** Si no, te dirá que no encuentra `claude`.
2. Verifica la instalación:
   ```
   claude --version
   ```
   Debe responder con un número de versión.
3. Escribe `claude` y presiona Enter. La primera vez te pide escoger colores y **entrar con tu cuenta de Claude** (se abre el navegador).

<a id="sin-pro"></a>

> **¿No tienes Claude Pro?** Claude Code también funciona con una cuenta de la
> [Claude Console](https://platform.claude.com), que se paga por uso. Al entrar, escoge
> "Anthropic Console" en vez de tu cuenta de claude.ai. Antes de empezar, ponle un **límite de
> gasto** en la Console: cada pregunta cuesta.

<a id="paso-3"></a>

### Paso 3. Los modos de permiso

Claude Code te deja escoger cuánta libertad le das. Cambias de modo con **Shift+Tab**, y el modo
activo se ve abajo en la terminal.

| Modo | Qué hace Claude | Cuándo usarlo |
|---|---|---|
| **Manual** | Te pide permiso antes de cambiar un archivo o correr un comando | Cuando empiezas o algo es delicado |
| **Auto-aceptar** | Edita archivos sin preguntar; los demás comandos sí los pregunta | Cuando ya aprobaste el plan y quieres velocidad |
| **Plan** | Solo lee y explora, no cambia nada. Al final te propone un plan | Para investigar o antes de construir |
| **Auto** | Trabaja sin preguntar; un revisor automático bloquea lo peligroso | Cuando ya confías en el flujo (lo vemos en la sesión 2) |

La regla: **plan para pensar, auto-aceptar para construir, manual cuando no estás seguro.**
Entre menos te pregunta, más fácil se le pasa un error sin que lo veas.

<a id="parte-1"></a>

## Parte 1 · Explorar: desarma Spliit

[Splitwise](https://www.splitwise.com) es una app para dividir gastos entre amigos, y cobra por
varias de sus funciones. **Spliit** es una alternativa de **código abierto** (licencia MIT): su
código es público y se puede leer, estudiar y usar para aprender. Por eso desarmamos Spliit y no
Splitwise: **antes de desarmar una app, mira su licencia.**

<a id="paso-4"></a>

### Paso 4. Conecta REA

[REA](https://rea.tools) es una caja de herramientas para desarmar software que se le conecta a
Claude Code. En la terminal (fuera de Claude Code):

```
mkdir rea-work && cd rea-work
git clone https://github.com/spliit-app/spliit.git
npx rea-agents@latest setup --client claude_code
```

El `setup` te muestra lo que va a cambiar y te pide aprobarlo. Después **cierra Claude Code si lo
tenías abierto** y verifica:

```
npx -y rea-agents@latest doctor --client claude_code
```

✅ **Victoria 1** cuando diga `healthy: true`.

<a id="paso-5"></a>

### Paso 5. Pregúntale a Spliit cómo funciona

Abre Claude Code **en modo plan**, para que solo pueda mirar:

```
claude --permission-mode plan
```

Pega este prompt:

> Usa REA para analizar la app que está en la carpeta spliit. Explícame como si no supiera programar: ¿qué pantallas tiene y qué guarda?

Cuando responda, pega este:

> Con REA, encuentra cómo Spliit calcula quién le debe a quién. ¿Qué formas de dividir un gasto tiene? Muéstrame los archivos y las líneas.

✅ **Victoria 2** cuando Claude te explique quién le debe a quién. ¿Cuántas formas de dividir encontró?

<a id="mesa"></a>

## La mesa de trabajo (ventana de contexto)

Escribe esto en Claude Code:

```
/context
```

Te muestra cuánto se ha llenado su **ventana de contexto**. Piénsala como la mesa de trabajo de
Claude: todo lo que lee queda encima (tus mensajes, los archivos, lo que responde cada comando). La
mesa es grande, pero no infinita. Cuando se llena, Claude resume lo de abajo para hacer espacio, y en
el resumen se pierden detalles. Por eso:

1. **Una tarea, una sesión.** Desarmar Spliit y construir tu app son dos tareas: la siguiente parte empieza en una sesión nueva.
2. **Pregunta concreto.** "Analiza todo" llena la mesa; "¿cómo calcula quién debe a quién?" trae solo lo necesario.
3. **Mira la mesa** con `/context` de vez en cuando.

Sal de Claude Code con `/exit`.

<a id="parte-2"></a>

## Parte 2 · Planear

<a id="paso-6"></a>

### Paso 6. Una carpeta nueva para tu app

Sal de la carpeta `rea-work` y crea la de tu app:

```
cd ..
mkdir mi-splitwise && cd mi-splitwise
git init
claude
```

<a id="paso-7"></a>

### Paso 7. Pídele un plan

Presiona **Shift+Tab** hasta que veas el modo plan abajo. Pega este prompt:

> Quiero una app de dividir gastos entre amigos, en un solo archivo index.html, inspirada en lo que aprendimos de Spliit. Debe permitir: agregar personas, registrar un gasto (quién pagó, cuánto, entre quiénes, en partes iguales) y mostrar quién le debe a quién con la menor cantidad de pagos. Guarda los datos en el navegador y que se vea bien en el celular. No uses el nombre ni el logo de Splitwise ni de Spliit. Sabremos que funciona si: con Ana, Beto y Caro, Ana paga 90.000 de una cena entre los tres, y la app dice que Beto y Caro le deben 30.000 cada uno a Ana. Antes de escribir código, hazme las preguntas que necesites.

Fíjate en lo que tiene un buen prompt: **qué quieres, qué debe hacer, cómo sabremos que funciona**
y una invitación a que te pregunte. Responde sus preguntas y **lee el plan**: es el mejor momento
para corregir, porque todavía no existe el código. Si algo no te convence, pídele que lo cambie
antes de aprobar.

<a id="parte-3"></a>

## Parte 3 · Codificar

<a id="paso-8"></a>

### Paso 8. Aprueba el plan y pruébala

Cuando el plan te guste, apruébalo escogiendo **auto-aceptar ediciones**: Claude construye sin
pedirte permiso archivo por archivo. Si ves que se desvía, presiona **Esc** y corrígelo.

Cuando termine, abre tu app en el navegador:

- **Mac:** `open index.html`
- **Windows:** `start index.html`
- **Linux:** `xdg-open index.html`

Prueba el caso de Ana, Beto y Caro. **Claude se equivoca:** puede entenderte mal, meter errores o
hacer cosas que no pediste. Tú pruebas. Si algo falla, díselo con un ejemplo concreto y pide los
ajustes de a uno.

✅ **Victoria 3** cuando registres un gasto y te diga quién debe cuánto.

<a id="parte-4"></a>

## Parte 4 · Commit

<a id="paso-9"></a>

### Paso 9. Revisión y commit

Un **commit** es una foto de tu proyecto a la que siempre puedes volver. Antes de tomarla:

1. **Pruébala tú** con un caso propio (por ejemplo, un gasto entre cuatro personas).
2. Presiona **Shift+Tab** hasta volver a modo manual, y pega:

> Revisa con ojos frescos lo que hicimos, como si no lo hubieras escrito tú: ¿hay errores en las cuentas o casos que se rompan? Si todo está bien, haz el commit con un mensaje en español que explique qué hace la app.

3. Lee lo que va a hacer y apruébalo. Después, fuera de Claude Code o con `!` adelante:

```
git log
```

✅ **Victoria 4** cuando veas tu commit.

<a id="taller"></a>

## Taller

1. **Divide por porcentajes**, como Spliit. Usa el mismo método: plan primero, después código, después commit.
2. **Memoria entre sesiones:** escribe `/init` en Claude Code (crea un archivo `CLAUDE.md` con lo que sabe de tu proyecto). Cierra Claude Code, ábrelo otra vez y pídele una mejora. ¿Se acordó de tu app sin explicarle?
3. **Reto:** que los gastos se compartan entre varios teléfonos. Pista: necesitas una base de datos, como la de la [sesión 3 del Nivelatorio](../../sesiones/03/).

<a id="problemas"></a>

## Problemas frecuentes

| Problema | Solución |
|---|---|
| `command not found: claude` o "no se reconoce" | Cierra la terminal y abre una nueva. Si sigue, repite el [paso 1](#paso-1). |
| Windows: `'irm' is not recognized` | Estás en CMD, no en PowerShell. Usa el comando de CMD del [paso 1](#paso-1). |
| Windows: `The token '&&' is not a valid statement separator` | Estás en PowerShell. Usa el comando de PowerShell. |
| `EBADENGINE` al usar REA | Tu Node es viejo. Instala la versión LTS de [nodejs.org](https://nodejs.org). |
| Claude Code dice que tu plan no incluye Claude Code | Estás con el plan gratis. Necesitas Pro, Max o una [cuenta de la Console](#sin-pro). |
| REA no aparece en Claude Code | Cierra Claude Code y vuelve a abrirlo después del `setup`. Corre el `doctor` del [paso 4](#paso-4). |
| La app no hace bien las cuentas | Dale a Claude el caso exacto que falla ("con estos gastos dice X y debería decir Y"). |

<a id="glosario"></a>

## Glosario

- **Agente:** un asistente de IA que actúa (usa herramientas, cambia archivos, corre comandos) para lograr una meta, y verifica su trabajo.
- **Claude Code:** el agente de Claude que trabaja dentro de una carpeta de tu computador.
- **Terminal:** la ventana donde le das instrucciones al computador escribiendo comandos.
- **Modo plan:** el modo en que Claude solo mira y propone; no cambia nada.
- **Auto-aceptar:** el modo en que Claude edita archivos sin pedirte permiso cada vez.
- **Ventana de contexto:** la "mesa de trabajo" de Claude: todo lo que puede tener presente a la vez.
- **REA:** herramientas para desarmar software, conectadas a Claude Code.
- **Código abierto:** software cuyo código es público y se puede estudiar y reutilizar según su licencia.
- **Commit:** una foto guardada de tu proyecto, con un mensaje que dice qué cambió.

---

[Inicio](../../)
