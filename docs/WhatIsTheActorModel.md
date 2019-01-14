# ¿Qué es el modelo de actor?

Las características de los entornos informáticos de hoy en día son muy diferentes de las que se utilizaron cuando se concibieron los modelos de programación antiguos. Los actores fueron inventados hace décadas por Carl Hewitt. Pero relativamente recientemente, su aplicabilidad a los desafíos de los sistemas informáticos modernos ha sido reconocida y ha demostrado ser efectiva.

El modelo de actor proporciona una abstracción que le permite pensar en su código en términos de comunicación, al igual que las personas en una gran organización. La característica básica de los actores es que modelan el mundo como entidades de estado que se comunican entre sí mediante el paso explícito de mensajes.

Como entidades computacionales, los actores tienen estas características:

  + Se comunican con mensajes asíncronos en lugar de llamadas a métodos.
  + Ellos manejan su propio estado.
  + Al responder a un mensaje, pueden:
    + Crear otros actores (hijos).
    + Enviar mensajes a otros actores.
    + Detener a los actores(hijos) o ellos mismos.
