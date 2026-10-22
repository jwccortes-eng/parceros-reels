# parceros-reels

Almacén público de los Reels de **@parcerosapps** listos para publicar, y la cola que usa la tarea diaria de Claude.

## Cómo funciona

1. Claude renderiza cada Reel (marca, subtítulos, cierre) y lo sube a `reels/`.
2. `queue.json` guarda, por Reel: archivo, caption, primer comentario y estado.
3. Jorge revisa y aprueba (`status: "approved"`). Nada se publica sin aprobación previa del video + caption exactos.
4. Todos los días a las **7:00 pm (NY)** la tarea programada toma el **primer** item `approved`, lo importa a vidIQ desde el enlace `raw.githubusercontent.com`, lo publica en Instagram y marca el item como `published` con el permalink.

## Estados

| status | significado |
|---|---|
| `pending_approval` | renderizado, esperando el OK de Jorge |
| `approved` | listo; la tarea diaria lo publica en el siguiente turno |
| `hold` | aprobado pero no publicar todavía |
| `published` | ya salió (tiene `permalink`) |

## Para pausar un día
Cambia el `status` del siguiente item a `hold`, o simplemente no dejes ninguno en `approved`.

## Enlace público de un Reel
`https://raw.githubusercontent.com/jwccortes-eng/parceros-reels/main/reels/<archivo>.mp4`
