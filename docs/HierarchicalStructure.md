# Estructura jerárquica

Como en una organización económica, los actores naturalmente forman jerarquías. Un actor, que supervisa una determinada función en el programa, podría querer dividir su tarea en partes más pequeñas y manejables. Para ello se inicializa los actores hijos que supervisa. Es importante conocer que cada actor tiene exactamente un supervisor, que es el actor que lo creó.

La característica esencial de los sistemas de actores es que las tareas se dividen y se delegan hasta que se vuelven lo suficientemente pequeñas como para ser manejadas en una sola pieza. Al hacerlo, no solo la tarea en sí está claramente estructurada, sino que los actores resultantes pueden razonarse en función de qué mensajes deben procesar, cómo deben reaccionar normalmente y cómo deben manejarse las fallas. Si un actor no tiene los medios para enfrentar una determinada situación, envía un mensaje de falla correspondiente a su supervisor, pidiéndole ayuda. La estructura recursiva permite entonces manejar la falla en el nivel correcto.

![jerarquía](https://getakka.net/images/ErrorKernel.png)

Compare esto con el diseño de software en capas que se convierte fácilmente en programación defensiva con el objetivo de no filtrar ninguna falla: si el problema se comunica a la persona correcta, se puede encontrar una mejor solución que si se intenta mantener todo "debajo de la alfombra".

Ahora, la dificultad de diseñar un sistema de este tipo es cómo decidir quién debe supervisar qué. Por supuesto, no existe una mejor solución, pero hay algunas pautas que podrían ser útiles:

  + Si un actor maneja el trabajo que otro actor está haciendo, por ejemplo, Al pasar las subtareas, el padre debe supervisar al hijo.    La razón es que el padre sabe qué tipo de fallas se esperan y cómo manejarlas.
  + Si un actor transporta datos muy importantes (es decir, su estado no se perderá si es evitable), este actor debería proporcionar     cualquier sub-tarea posiblemente peligrosa a los hijos que supervisa y manejar las fallas de estos hijos según sea apropiado. Dependiendo de la naturaleza de las solicitudes, puede ser mejor crear un nuevo hijo para cada solicitud, lo que simplifica la administración del    estado para recopilar las respuestas. Esto se conoce como "Error Kernel Pattern" de Erlang.
  + Si un actor depende de otro para cumplir con su deber, debe vigilar la vida de ese otro actor y actuar al recibir un aviso de terminación. Esto es diferente de la supervisión, ya que la parte observadora no tiene influencia en la estrategia del supervisor, y debe tenerse en cuenta que una dependencia funcional por sí sola no es un criterio para decidir dónde colocar a un determinado actor hijo en la jerarquía.

Por supuesto, siempre hay excepciones a estas reglas, pero no importa si las sigues o las rompes, siempre debes tener una razón.
