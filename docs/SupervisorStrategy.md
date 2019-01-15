La pieza final de un actor es su estrategia para manejar las faltas de sus hijos. Akka realiza la gestión de fallas de manera transparente, aplicando una de las estrategias descritas en Supervisión y monitoreo para cada falla entrante. Como esta estrategia es fundamental para estructurar el sistema de un actor, no se puede cambiar una vez que se haya creado un actor.

Teniendo en cuenta que solo existe una estrategia de este tipo para cada actor, esto significa que si se aplican diferentes estrategias a los distintos hijos de un actor, los niños deben agruparse bajo supervisores intermedios con estrategias de emparejamiento, prefiriendo una vez más la estructuración de los sistemas de actores según la División de tareas en sub-tareas.

```csharp 
            protected override SupervisorStrategy SupervisorStrategy()
            {
                return new OneForOneStrategy(10, TimeSpan.FromSeconds(30),
                    x =>
                    {
                    if (x is ArithmeticException) return Directive.Resume;

                    else if (x is NotSupportedException) return Directive.Stop;

                    else return Directive.Restart;
                    });
            }

 ```
