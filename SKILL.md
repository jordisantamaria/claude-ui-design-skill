---
name: ui-design
description: Cómo tomar las decisiones visuales de una pantalla — jerarquía, tipografía, color, espaciado, profundidad — y cómo reparar las que ya están mal. Vale para web y para móvil. Se usa ANTES y MIENTRAS se escribe UI, no después. Cada proyecto aporta sus datos en un `ui-profile`. Triggers - "/ui-design", "diseña esta pantalla", "esto se ve mal", "mejora el diseño de", "arregla la UI de", o al empezar o retocar cualquier pantalla o componente.
---

# UI Design

*© 2026 Jordi Santamaria Portoles. CC BY 4.0 — uso y adaptación libres citando al autor.
Original: https://github.com/jordisantamaria/claude-ui-design-skill*

Todo lo que necesitas para decidir está aquí. Si algo de esta skill te parece discutible,
discútelo con la pantalla que tienes delante, no busques una autoridad que lo respalde.

Documento vivo: arrancó en septiembre de 2026 y crece con cada pantalla que sale mal. Ver
**Mantenimiento** antes de añadirle nada.

## Lo primero: carga el perfil de este proyecto

Esta skill lleva el criterio. Los **datos** —paleta, escala, plataforma, utilidades, qué
está roto hoy— son de cada repo y viven en su perfil. Búscalo en este orden y léelo antes
de tocar nada:

1. `<repo>/.claude/ui-profile.md` — el del proyecto
2. `~/.claude/ui-profiles/<nombre-del-repo>.md` — el personal, para repos de otros

**Si no hay perfil, no improvises tokens.** Mide primero (apartado 9) y escribe el perfil: media
hora ahí evita meses de decisiones inventadas. Si el usuario tiene prisa, aplica solo lo
que no depende de tokens —jerarquía y espaciado— y dilo.

## Qué es esta skill y qué NO es

Pregunta **¿se entiende de un vistazo?**, y corre ANTES y MIENTRAS. Si llegas aquí con la
pantalla ya escrita, llegas tarde y toca rehacer decisiones.

No es un gate de usabilidad. Si el proyecto tiene uno, eso corre DESPUÉS y pregunta otra cosa: si además de verse bien, funciona. Teclado, estados
vacíos, errores, foco, lectores de pantalla. Las dos hacen falta y no se pisan.

## El código que ya hay NO es la referencia

Esto va primero porque es el reflejo más fuerte: al escribir una pantalla, abres el fichero
de al lado y sigues su estilo. En un proyecto con deuda visual, eso propaga el defecto.

El perfil de cada repo trae su lista de lo que está roto, medido. **Mientras esos números
no bajen, cuando un fichero existente contradiga esta skill, manda la skill.** Copiar el
gris ilegible del componente vecino no es respetar una convención: es heredar un bug.

## 1. Jerarquía: es el trabajo, no el adorno

Cuando todo compite por la atención, la pantalla se lee como un muro. Antes de escribir
nada decide **qué es lo primario**, qué es secundario y qué es terciario. Una pantalla tiene
UN elemento primario. Si tiene dos, no has decidido.

**El tamaño es el último recurso, no el primero.** Para destacar algo, en este orden:

1. **Peso** — semibold. Deja el tamaño donde está.
2. **Color** — sube el contraste del primario; no bajes el del resto por debajo de AA.
3. **Tamaño** — solo si 1 y 2 no bastan.

Encoger y aclarar son las dos maneras equivocadas de hundir algo: las dos se pagan en
legibilidad. Subir el peso de lo primario es gratis. Para hundir, color más suave primero
—sin salirse de AA— y tamaño después.

Dos pesos bastan para UI: uno normal y uno fuerte. **Nunca por debajo del normal**: a
tamaños pequeños un peso ligero no se lee, y menos en CJK.

**Destaca hundiendo lo de al lado.** Si el elemento principal no resalta y ya no le puedes
añadir nada, quítale a sus vecinos. Un item activo destaca más cuando los inactivos se
apagan que cuando el activo se enciende. Vale también para bloques enteros: si una barra
lateral compite con el contenido, quítale el fondo en vez de darle más al contenido.

**Las etiquetas son el último recurso.** El formato ya suele decir qué es un dato:
`2026-09-08` es una fecha, `¥3,000` un precio, `a@b.com` un correo. Cuando no basta el
formato, casi siempre basta el contexto. Y cuando hace falta, fúndela con el valor —«12 en
stock» en vez de «Stock: 12»— o trátala como apoyo: más pequeña y más suave que el dato.
La excepción es la pantalla densa de datos donde se **busca la etiqueta** (una tabla de
especificaciones): quien la mira escanea buscando «profundidad», no «7,6 mm», así que ahí
la etiqueta se lee primero y no se hunde.

**Los iconos pesan.** Un icono sólido junto a texto cubre más superficie y se come la
atención. Si desequilibra, bájale el contraste. Y al revés: un borde de 1px demasiado sutil
se arregla engordándolo antes que oscureciéndolo.

**Las acciones tienen pirámide.** Primaria: sólida, alto contraste, una por pantalla.
Secundaria: contorno o fondo suave. Terciaria: estilo de enlace. Una acción destructiva no
es automáticamente roja y grande: si no es la principal, va como secundaria o terciaria, y
el rojo grande se reserva para el paso de confirmación.

**La jerarquía visual no es la del documento.** El nivel semántico de un encabezado dice
qué es, no cómo de grande va. Muchos títulos de sección funcionan como etiquetas: el
contenido es el protagonista, no el rótulo.

**La forma de un componente no viene dada.** Saber qué props tiene un `Select` no es lo
mismo que saber qué forma debe tener aquí. Un desplegable no está obligado a ser una lista
de enlaces en una caja blanca: puede llevar secciones, dos columnas, texto de apoyo o
iconos. Unos radios que son la decisión central de la pantalla se leen mucho mejor como
tarjetas seleccionables que como una pila de circulitos. Una tabla puede fusionar dos
columnas relacionadas —si esa columna no necesita ordenarse— y ganar jerarquía. La regla:
usa el componente de la librería como base, pero **no heredes su forma por defecto sin
preguntarte si es la que este contenido pide**.

## 2. Texto

**Escala corta, con un papel por escalón.** No es «todo grande»: es que cada tamaño tenga
un trabajo. La escala concreta está en el perfil; los papeles son siempre estos:

| | Para qué |
|---|---|
| Cuerpo | Lo que se ha venido a leer |
| Apoyo | Lo que aún se lee entero: descripción secundaria, subtítulo |
| Metadato | Una unidad, un contador, una fecha auxiliar junto a un dato que ya se entiende |

**El escalón de metadato nunca debe ser el más usado.** Si lo es, lo que hay ahí ya no son
metadatos: es el contenido, escrito demasiado pequeño.

**«No cabe» casi nunca se arregla encogiendo.** Si una pantalla no cabe, sobra contenido o
falta jerarquía. Encogerlo todo por igual paga legibilidad sin comprar separación, porque
la proporción entre elementos no cambia. Peso fuerte + color oscuro junto a peso normal +
color medio separa mucho más que dos tamaños distintos, y ocupa casi lo mismo: **el
contraste de peso y de color es gratis en píxeles, el de tamaño no.**

**Interlineado inversamente proporcional al tamaño**, y proporcional a la longitud de línea.
Texto pequeño o líneas largas necesitan más aire; un titular grande puede ir a 1.

**Longitud de línea**: 45-75 caracteres en alfabeto latino. **En japonés, 15-25** — un
párrafo japonés a lo ancho de una pantalla grande cansa mucho antes que uno inglés.

**Alineación**: a la izquierda por defecto. Centrado solo para bloques de una o dos líneas
—si se va a tres, la solución es reescribirlo más corto—. Números en tabla, a la derecha,
para que los decimales caigan en la misma columna.

**Baseline, no centro.** Al mezclar dos tamaños en la misma línea, alinéalos por la línea
base, no por el centro. Es una referencia que el ojo ya percibe.

**`letter-spacing`**: déjalo como viene. Las dos excepciones son latinas: apretar un
titular de una tipografía pensada para texto pequeño, y airear texto en mayúsculas, que sin
ello se lee peor. **En CJK no se toca nunca**: rompe el ritmo de la caja.

## 3. Color

**El contraste es un número, no una opinión.** AA pide 4.5:1 para texto normal y 3:1 para
texto grande y para el grafismo que identifica un control. No lo estimes a ojo: calcúlalo.
Si el proyecto tiene un test de contraste, es el árbitro.

**Necesitas más colores de los que crees**: 8-10 grises, 5-10 tonos de cada primario, y
acentos para estados. Con cinco hex no se construye nada. Y defínelos por adelantado en vez
de generar variantes al vuelo con `lighten`/`darken`, que es como se acaba con 35 azules
casi iguales.

**Gris sobre fondo de color, no.** Aclarar el texto funciona sobre blanco porque lo que
haces en realidad es bajar contraste. Sobre color, un gris se ve sucio, y blanco con
opacidad se ve apagado o deshabilitado —y sobre una imagen, el fondo se transparenta a
través del texto—. Elige el color a mano: mismo tono que el fondo, ajusta saturación y
luminosidad hasta que quede.

**Para texto de color sobre fondo de color**, si no llegas al ratio sin acercarte al blanco,
gira el tono hacia uno más brillante (cian, magenta, amarillo) en vez de subir la
luminosidad. Y al revés: si el fondo oscuro que exige AA te roba el protagonismo de la
pantalla, invierte —texto de color oscuro sobre fondo de color claro— en vez de oscurecer
el fondo.

**Los grises no tienen que ser grises.** Un punto de azul los enfría, un punto de amarillo
los calienta. Sube la saturación en los extremos de la escala o los tonos claros y oscuros
se ven lavados.

**El color nunca comunica solo.** Un estado, una tendencia o un aviso necesitan además
icono, texto o posición. Vale por daltonismo, y también porque el color se pierde a plena
luz — decisivo si la app se usa en la calle.

## 4. Espaciado

**Empieza sobrado y quita.** El aire se resta, no se suma: si lo añades, te quedas siempre
en el mínimo para que no se vea mal, que está lejos de verse bien. La excepción deliberada
es la pantalla densa de datos, donde apretar es la decisión correcta — pero que sea una
decisión, no el resultado de no haber pensado.

**Escala corta, y sin valores indistinguibles.** Entre dos valores contiguos tiene que
haber un 25% largo. Si tu escala te deja elegir entre 12 y 14, no te está ayudando a
decidir: te está cobrando una decisión que nadie va a percibir.

**Espaciado ambiguo = bug de lectura.** Siempre más espacio ALREDEDOR de un grupo que
DENTRO de él. Si el hueco entre una etiqueta y su campo es igual que el hueco hasta el
campo siguiente, no se sabe qué va con qué — y en un formulario eso acaba en el dato
escrito en la casilla equivocada. Pasa igual en listas y en encabezados de sección.

**No estires porque hay sitio.** Dale a cada elemento el ancho que necesita, no el que
sobra. Y no escales todo en proporción: al reducir el tamaño de pantalla, lo grande encoge
más deprisa que lo pequeño, y el padding de un botón grande es más generoso que el de uno
pequeño, no proporcional.

## 5. Profundidad

Por orden de coste, de más barato a más caro:

1. **Color** — más claro que el fondo se acerca, más oscuro se hunde. Funciona incluso en
   diseños planos y no cuesta nada.
2. **Bordes de acento** — una franja de color en el canto de una tarjeta, bajo un titular o
   al lado de un aviso da carácter sin saber dibujar. Es lo más rentable de esta lista:
   pruébalo antes que nada.
3. **Solapar** — que un elemento cruce la frontera entre dos fondos crea capas de verdad.
   Con imágenes, dales un borde del color del fondo para que no choquen entre sí.
4. **Sombra** — para lo que de verdad flota: un menú, un modal. Cuanto más grande y difusa,
   más cerca se siente y más atención roba, así que la escala de sombras es una escala de
   elevación: elige por dónde va el elemento en el eje Z, no por cómo queda la sombra.

Si simulas luz, que venga de arriba: borde superior más claro y sombra corta abajo para lo
que sobresale, y al revés para lo hundido. Sin pasarse — realismo fotográfico en una UI la
ensucia.

**Menos bordes.** Antes de separar dos cosas con un borde, prueba fondos ligeramente
distintos, una sombra suave, o simplemente más espacio. Un borde por cada separación deja
la pantalla sucia.

**Radio consistente.** Mezclar esquinas rectas y redondeadas en la misma pantalla se ve peor
que cualquiera de las dos opciones por separado. El valor está en el perfil.

## 6. Contenido que sube el usuario

No controlas su encuadre, ni su contraste, ni su fondo.

- **Fija la forma**: contenedor de tamaño fijo y recorte al centro, o el ratio original te
  desmonta la retícula.
- **Evita que el fondo se funda**: una imagen de fondo claro sobre un fondo claro pierde su
  silueta. Una sombra interior sutil la perfila mejor que un borde, que choca con los
  colores de la imagen.
- **Texto encima de una foto: casi siempre, no.** Antes de resolver *cómo* ponerlo encima,
  pregúntate si tiene que ir encima. Distingue dos casos, porque se tratan al revés:
  - **La imagen es decoración** (un hero, una portada de marketing): está ahí para sostener
    el mensaje, así que el texto encima es lo normal.
  - **La imagen es el contenido** (una foto que ha subido alguien): ha venido a *verla*.
    Cada píxel de UI encima —un texto, un degradado, una capa oscura, un botón— le tapa lo
    que quería mirar y empeora la experiencia. El sitio del texto es fuera: debajo, al
    lado, o en una barra que se pueda ocultar.

  Cuando de verdad tenga que ir encima —un marcador pequeño, un control efímero—, que sea
  lo mínimo, que se pueda ocultar, y entonces sí: **el problema no es el texto, es la
  imagen**. Bájale el contraste, ponle una capa semitransparente, tíñela de un color, o
  dale al texto una sombra difusa sin desplazamiento, que se lea como halo y no como sombra.
- **Cada dibujo tiene un tamaño para el que está hecho, y el SVG no salva eso.** Que sea
  vectorial evita el pixelado, no el problema: un icono dibujado para 24px lleva un grosor
  de trazo y un nivel de detalle elegidos para 24px, y al escalarlo **el trazo escala con
  él**. Un trazo de 1,8 a 24px es proporcionado; el mismo icono a 72px lleva un trazo de
  5,4, que se ve basto — y su geometría, simplificada al máximo para leerse pequeña, a
  tamaño grande se ve pobre y vacía. Es lo mismo que pasa con las tipografías, que también
  son vectoriales: una de display no funciona a 10px y una de texto se ve tosca a 100px.
  Hacia abajo pasa lo contrario: ese trazo de 1,8 a 12px queda por debajo de 1px físico y
  se difumina, y un logo detallado encogido a favicon se empasta.

  Si hay que llenar un hueco grande, mete el icono **a su tamaño** dentro de una forma con
  fondo, o usa uno dibujado para ese tamaño. Y una captura de pantalla completa encogida al
  70% no se lee: recorta un trozo, o hazla a un ancho menor.

## 7. Qué cambia entre web y móvil

**Móvil**
- No hay hover. Su equivalente es el estado *pressed*: al pulsar, el elemento se hunde
  (sombra más pequeña, o ninguna).
- Las unidades (`dp`, `pt`, `sp`) ya están calibradas a la distancia de uso de un móvil. La
  cercanía de la pantalla **no** es un descuento extra para bajar tamaños: ya está contada.
  Por eso las guías piden cuerpo grande, no pequeño — iOS 17pt, Material 16sp, y en las dos
  12 es la talla de *caption*, no la de cuerpo.
- El texto escala con el ajuste del sistema salvo que lo desactives, y en iOS llega al 310%.
  Una pantalla que solo cabe con el texto al mínimo ya está rota en el móvil de quien tenga
  el tamaño de fuente subido.
- El área de toque mínima es 44×44pt (iOS) / 48×48dp (Android), independientemente de lo
  pequeño que sea el icono que hay dentro.

**Web**
- El hover existe: úsalo para lo secundario. Un enlace auxiliar puede revelar su subrayado
  solo al pasar por encima, en vez de competir siempre.
- Las rejillas de 12 columnas reparten porcentajes. No todo debe ser fluido: lo que tiene
  un ancho óptimo (una barra lateral, una tarjeta de login) va a ancho fijo o `max-width`,
  y solo encoge cuando la pantalla baja de ahí.
- `em` para tamaños de fuente compone mal —anidas dos y ya no estás en tu escala—: usa `px`
  o `rem`. Para anchos de párrafo sí es útil, porque va con el tamaño del texto.
- Que la ventana sea ancha no obliga a llenarla.

**Lo que NO está aquí, a propósito**: el catálogo de Material, la HIG entera, la API de
cada componente. Eso se consulta cuando hace falta y no gana nada por estar escrito. Lo que
sí está son los pocos números duros que se incumplen en la práctica, no por no saberlos
—el de 44pt lo sabe cualquiera— sino porque en el momento de dibujar un icono de 24px nadie
se los pregunta.

**Y lo versionado se consulta, no se recuerda.** Los tokens de Material cambiaron de M2 a
M3, iOS cambió de fondo con Liquid Glass, y MUI no se comporta igual en v5 que en v6. Si una
decisión depende de un detalle de una versión concreta —el nombre de un token, la altura de
un componente del sistema, un default— **míralo en la documentación de esa versión**. Un
número recordado de memoria y presentado con seguridad es peor que no darlo.

## 8. Reparar lo que ya está escrito

En un proyecto con deuda, casi todo el trabajo de UI es reparación, no obra nueva. Dos
categorías, y confundirlas es el error caro:

**Lo que se arregla en barrido**, porque no depende del contexto: un color ilegible lo es en
cualquier pantalla, y dos valores de espaciado indistinguibles lo son en cualquier pantalla.
Sustitución con criterio fijo, sin abrir la app.

**Lo que NO se puede barrer: la jerarquía.** Qué es lo primario de una pantalla es una
propiedad de esa pantalla. No hay `sed` que lo decida. Esto va pantalla a pantalla,
mirándola.

**El orden**: color primero (es lo que impide leer, y es barrido) → tamaño y peso juntos y
por pantalla, porque son la misma decisión → espaciado → radios.

**Cómo no romperlo**

- **Un `replace_all` sobre un color es peligroso**: cambia solo donde el color es **texto**,
  no donde es borde, fondo o parte de un degradado decorativo.
- **El mismo token puede estar bien en otro papel.** Un gris que falla como texto (4.5:1)
  puede cumplir de sobra como icono o borde (3:1). Se arregla el uso, no el token, salvo
  que el token esté mal en todos sus papeles.
- **Cada tanda pasa por el gate de usabilidad del proyecto**, si lo hay. Subir tamaños de
  fuente cambia alturas: es la forma más fácil de estrenar un bug de recorte o de solape.
- **Y se mira en un dispositivo real**, no solo en el simulador.

## 9. Cómo se escribe el perfil de un proyecto

Un perfil son los datos que esta skill no puede saber. Para escribirlo, mide — no supongas.
Cuenta las clases o los tokens que el proyecto usa de verdad y ordénalos por frecuencia:
tamaños de fuente, pesos, colores de texto, valores de espaciado, radios, sombras. Los
números salen de ahí, y de ellos sale la lista de lo que está roto.

Un perfil tiene:

1. **Plataforma y stack** — y qué implica (densidad de datos, CJK, modo oscuro, offline…).
2. **Los sistemas reales** — la escala tipográfica con el papel de cada escalón, la paleta,
   la escala de espaciado, los radios.
3. **Las utilidades que ya existen** — funciones de contraste, componentes base, tokens.
   Que nadie reimplemente lo que ya está.
4. **El estado medido, con fecha** — qué está roto y cuánto, y cómo tiene que quedar.
5. **Las decisiones firmadas** — la excepción que alguien ya tomó a conciencia, con el
   motivo. Sin esto, cada revisión reabre la misma discusión.
6. **El gate del proyecto**, si lo hay, y qué cubre él para no duplicarlo aquí.

## Mantenimiento

**De dónde salió el arranque.** Las reglas iniciales son una destilación de *Refactoring UI*
(Adam Wathan y Steve Schoger), traducidas a código y calibradas contra medidas reales. Eso
es el origen, no el límite: **esto no es «Refactoring UI»**, es el criterio de diseño de
estos proyectos, y a partir de aquí crece por su cuenta. Una regla no vale más ni menos por venir
de ese libro.

**Cómo entra una regla nueva.** Con un caso real detrás: una pantalla que salió mal, un
comentario de quien la usa, algo que se rehízo dos veces. Al añadirla, apunta de dónde sale.
Una regla que solo tiene una cita detrás y ningún caso todavía no se ha ganado el sitio.

**Aquí solo va lo universal.** Si una regla necesita nombrar un token, una clase o un
fichero, no es de esta skill: es del perfil de ese proyecto. La prueba: ¿sirve igual en una
app móvil de consumo y en una tabla de datos empresarial? Si no, va al perfil.

**Y solo va lo que no se aplica solo.** Una skill no es una enciclopedia: es la lista de lo
que se olvida aplicar en el momento de decidir. Antes de añadir algo, pregúntate en cuál de
las tres cae:

- **Se consulta cuando hace falta** → fuera. La API de un componente, el catálogo de
  Material, la HIG entera. Saberlo de memoria no mejora ninguna decisión.
- **Se sabe pero no se aplica** → dentro. El área de toque de 44pt es el ejemplo: nadie la
  desconoce, y aun así se incumple al dibujar un icono de 24px.
- **Depende de una versión** → fuera, y con instrucción de mirarlo. Los tokens de Material,
  los defaults de MUI, lo que cambió en la última iOS. Un número recordado de memoria y
  dicho con seguridad hace más daño que no darlo.

**Qué se quita.** Una regla que lleva meses sin que nadie la incumpla ya es un hábito y solo
ocupa sitio. Y cuando una regla se pueda comprobar con un test, su sitio es el test; aquí se
queda solo la decisión que el test no puede tomar.

**Fuentes, según lleguen:**

- 2026-09-08 — arranque: *Refactoring UI* + medidas de `oshisuki-mobile` (app en producción).
