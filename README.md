# ui-design — una skill de Claude Code para las decisiones visuales de una pantalla

Cómo decidir jerarquía, tipografía, color, espaciado y profundidad, y cómo reparar lo que ya
está mal. Vale para web y para móvil. Se usa **antes y mientras** se escribe UI, no después.

La escribí porque un agente que diseña sin criterio produce pantallas planas: todo con el
mismo peso, grises que no se leen, espaciado ambiguo y ninguna acción principal. Son fallos
que se conocen y aun así se repiten en el momento de decidir. Eso es lo que hay aquí, y solo
eso: la skill no es una enciclopedia de Material ni la HIG entera.

## Qué esperar de ella

Es una ayuda, no una solución. Con la skill cargada, Claude deja de cometer los fallos que
se repiten —todo con el mismo peso, grises ilegibles, espaciado ambiguo, ninguna acción
principal—, pero de ahí no sale un buen diseño a la primera. Hace falta iterar: mirar el
resultado, decir qué no funciona y volver a pasar. Lo que hace la skill es que cada
iteración empiece más arriba, no que sobren las iteraciones.

Tampoco sustituye al contexto de producto. Qué tiene que hacer el usuario en esa pantalla y
qué dato es el importante no lo sabe ningún documento genérico: eso se lo das tú.

La voy actualizando según veo qué errores se repiten, así que crece con el uso. Si te pasa
uno que la skill no cubre, abre un issue con el caso.

## Instalación

```bash
git clone https://github.com/jordisantamaria/claude-ui-design-skill
mkdir -p ~/.claude/skills/ui-design
cp claude-ui-design-skill/SKILL.md ~/.claude/skills/ui-design/SKILL.md
```

Se invoca con `/ui-design`, y Claude la carga solo cuando el trabajo es de UI.

## Necesita un perfil por proyecto

La skill lleva el **criterio**; los **datos** de cada proyecto (paleta, escala tipográfica,
escala de espaciado, radios, utilidades que ya existen, qué está roto hoy) viven en un
`ui-profile` aparte:

- `<repo>/.claude/ui-profile.md` — el del proyecto
- `~/.claude/ui-profiles/<nombre-del-repo>.md` — el personal, para repos de otros

Sin perfil, Claude se inventa los tokens. El apartado 9 de la skill explica cómo escribirlo:
midiendo lo que el proyecto usa de verdad, no suponiendo.

## Idioma

El original está en español y es el que se mantiene. Claude lo entiende igual trabajando en
cualquier idioma. Si alguien quiere una traducción, bienvenida por PR.

## Origen

Las reglas iniciales son una destilación de *Refactoring UI* (Adam Wathan y Steve Schoger),
traducidas a instrucciones para un agente y calibradas contra medidas reales de
`oshisuki-mobile`, mi app en producción. A partir de ahí es un documento vivo: cada regla nueva entra con un caso real
detrás. Si una regla te parece discutible, discútela con la pantalla que tengas delante.

## Licencia

[CC BY 4.0](LICENSE). Se puede usar y adaptar, también comercialmente, citando al autor:

> ui-design skill — Jordi Santamaria Portoles — https://github.com/jordisantamaria/claude-ui-design-skill
