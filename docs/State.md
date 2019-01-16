# Estado

Los objetos del actor normalmente contendrán algunas variables que reflejan los posibles estados en los que puede estar el actor. Pueden ser un contador, un conjunto de _listeners_, solicitudes pendientes, etc. 

Estos datos son lo que hace que un actor sea valioso, y deben ser protegidos de la corrupción por otros actores. 

La buena noticia es que los actores Akka.NET conceptualmente tienen su propio _hilo_, que está completamente protegido del resto del sistema. Esto significa que, en lugar de tener que sincronizar el acceso mediante bloqueos, puede escribir el código de su actor sin preocuparse por la concurrencia. 

Detrás de escena, Akka.NET ejecutará conjuntos de actores en conjuntos de subprocesos reales (o `Thread`s ), donde normalmente muchos actores comparten un subproceso, y las invocaciones subsiguientes de un actor pueden terminar siendo procesadas en diferentes subprocesos. 

Akka.NET se asegura de que este detalle de implementación no afecte el _hilo virtual_ de cada actor.Tener un estado inconsistente es fatal, por lo tanto, cuando el actor falla y **es reiniciado por su supervisor, el estado se creará desde cero**, como al crear al actor por primera vez. Esto es para permitir la capacidad de **"self-healing"** del sistema. 

Opcionalmente, el estado de un actor se puede recuperar automáticamente al estado antes del reinicio persistiendo los mensajes recibidos y reproduciéndolos después del reinicio (para esto ver "Persistencia").