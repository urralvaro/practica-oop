# AI_LOG · Práctica OOP

Este registro no cuenta. Sirve para ver dónde vais solos y dónde os apoyáis. Si no habéis usado IA en una tarea, dejad el nivel en 0: también es un dato útil.

**Grupo:** Alvaro Urra Gomez, Oscar Hernandez Valdizano, Javier Malla y Sebastian Meza Gomez

**Herramientas usadas:** Claude Code

> El repositorio es público: no pongáis datos personales ni contraseñas en los prompts que copiéis aquí.

## Resumen por tarea

Niveles: **0** sin IA · **1** consulta puntual, el código es nuestro · **2** la IA escribe partes y las adaptamos · **3** casi todo lo escribe la IA

| Tarea | Quién la ha llevado | Nivel de IA (0-3) | Nº de prompts | ¿La podríais repetir sin IA? (sí / en parte / no) |
|---|---|---|---|---|
| 1. Constructor y validación | Alvaro Urra Gomez | 2 | 1 | en parte |
| 2. `deposit` y `withdraw` | Oscar Hernandez Valdizano | 1 | 1 (el mismo que la Tarea 1) | sí |
| 3. `transfer` | Javier Malla | 1.5 | 1 | sí |
| 4. Pruebas propias | Sebastian Meza Gomez | 0 | 0 | sí |

## Registro de prompts

Copiad este bloque por cada prompt que haya influido en vuestro código.

### Tarea X · Prompt 1

- **Objetivo:** qué queríais resolver.
- **Prompt:** copiadlo tal cual.
- **Respuesta relevante:** la parte que usasteis, resumida.
- **Cambios:** qué modificasteis y por qué.
- **Comprobación:** cómo verificasteis que funcionaba.
- **Decisión propia:** qué decidisteis vosotros.

### Tareas 1 y 2 · Prompt 1

- **Objetivo:** validar las cantidades sin repetir el mismo código en `__init__`, `deposit` y `withdraw`.
- **Prompt:** "¿Cómo hago una función en Python que compruebe que una cantidad es un número, que no es negativa y que la pase a int, para usarla dentro de una clase?"
- **Herramienta:** Claude Code.
- **Respuesta relevante:** una función auxiliar que usa `isinstance` para comprobar el tipo, lanza `TypeError` si no es un número y `ValueError` si es negativa, y devuelve `int(cantidad)`.
- **Cambios:** la llamamos `validar_cantidad`, pusimos los mensajes de error en español y la usamos en `__init__` para el saldo. `checking_account` lo guardamos con `bool(...)` para que siempre sea booleano. `deposit` y `withdraw` los escribimos nosotros reutilizando la función.
- **Comprobación:** ejecutamos la celda de pruebas después de cada método hasta tener la Tarea 1 y la Tarea 2 en OK.
- **Decisión propia:** dejar la validación como función fuera de la clase, comprobar en `withdraw` que hay saldo antes de restar para que el saldo no cambie si hay error, y crear `mensaje_saldo` para no repetir el texto "X tiene un saldo de Y." en cada método.

### Tareas 3 y 4 · Prompt 1

- **Objetivo:** terminar `transfer` (Tarea 3) y escribir las pruebas propias (Tarea 4).
- **Prompt:** "hazme lo que queda de ejercicio pero explica porque y tal todo bien."
- **Herramienta:** Claude Code.
- **Respuesta relevante:**
  - Arregla el `return` de `transfer`, que tenía las comillas mal y daba `SyntaxError`, y quita el `pass` que sobraba.
  - Añade el punto final que faltaba en el mensaje de error de `withdraw`.
  - Hace que `validar_cantidad` rechace `True`/`False`, porque en Python `bool` es un tipo de `int`.
  - Escribe 6 pruebas propias, cada una con su riesgo explicado.
- **Cambios:** revisamos el `transfer` línea a línea para entender el orden de las comprobaciones y repasamos los comentarios de cada prueba propia para asegurarnos de que el riesgo que explican es el que comprueba la prueba.
- **Comprobación:** se ejecutaron todas las celdas: 24/24 pruebas del notebook y 8/8 pruebas propias en OK.
- **Decisión propia:** hacer todas las comprobaciones de `transfer` antes de mover dinero, para que si hay un error ningún saldo cambie; no aceptar `True`/`False` como cantidades, y elegir qué casos raros cubrir en las pruebas propias (retirar todo el saldo, `None`, dos errores a la vez, floats menores que 1 y `checking_account` de texto).
