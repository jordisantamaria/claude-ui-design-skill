# Contribuir y mantener la skill

Estas son las reglas con las que la skill crece. No van dentro de `SKILL.md` porque no
ayudan a decidir nada al diseñar: solo ocuparían contexto en cada uso.

**De dónde salió el arranque.** Las reglas iniciales son una destilación de *Refactoring UI*
(Adam Wathan y Steve Schoger), traducidas a código y calibradas contra medidas reales. Eso
es el origen, no el límite: **esto no es «Refactoring UI»**, es un criterio de diseño propio
que a partir de aquí crece por su cuenta. Una regla no vale más ni menos por venir de ese
libro.

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

- *Refactoring UI* — Adam Wathan y Steve Schoger.
