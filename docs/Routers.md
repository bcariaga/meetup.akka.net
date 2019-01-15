Un enrutador es un tipo especial de actor cuyo trabajo es enrutar mensajes a otros actores llamados enrutados. Diferentes enrutadores utilizan diferentes estrategias para enrutar mensajes de manera eficiente.

Los enrutadores se pueden usar dentro o fuera de un actor, y usted puede administrarlos personalmente o usar un actor enrutador autónomo con capacidades de configuración, y también puede redimensionar dinámicamente bajo carga.

Akka.NET viene con varios enrutadores útiles que puede elegir de inmediato, de acuerdo con las necesidades de su aplicación. Pero también es posible crear el tuyo.

# Estrategias de enrutamiento

## RoundRobin

![roundRobin](https://getakka.net/images/RoundRobinRouter.png)

```csharp 
var workers = new [] { "/user/workers/w1", "/user/workers/w3", "/user/workers/w3" }
var router = system.ActorOf(Props.Empty.WithRouter(new RoundRobinGroup(workers)), "some-group");
 ```
 
 ## Broadcast

El enrutador BroadcastGroup, como su nombre lo indica, transmitirán cualquier mensaje a todos sus enrutadores.

![broadcast](https://getakka.net/images/BroadcastRouter.png)

```csharp 
var actors = new [] { "/user/a1", "/user/a2", "/user/a3" }
var router = system.ActorOf(Props.Empty.WithRouter(new BroadcastGroup(actors)), "some-group");
```

Para ver más enrutadores pueden visitar este enlace: https://getakka.net/articles/actors/routers.html#routing-strategies

