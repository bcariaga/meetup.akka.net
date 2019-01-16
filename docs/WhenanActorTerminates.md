Cuando un actor termina 

Una vez que un actor termina, es decir, falla de una manera que no es manejada, por un reinicio, se detiene a sí mismo o es detenida por su supervisor, liberará sus recursos, drenando todos los mensajes restantes de su buzón en el "buzón de correo no deseado" del sistema que los reenviará a `EventStream` como `DeadLetters`. 

El buzón se reemplaza dentro de la referencia del actor por un buzón del sistema, redirigiendo todos los mensajes nuevos a EventStream como DeadLetters. Sin embargo, esto se hace sobre la base _"del mejor esfuerzo"_, así que no hay qeu confiar en eso para construir una _"entrega garantizada"_.

La razón para no solo volcar silenciosamente los mensajes se inspiró en nuestras pruebas: registramos el TestEventListener en el bus de eventos al que se envían las letras muertas, y eso registrará una advertencia por cada letra muerta recibida; esto ha sido muy útil para descifrar Fallos de prueba más rápidamente. 
Es posible que esta característica también pueda ser utilizada para otros fines.