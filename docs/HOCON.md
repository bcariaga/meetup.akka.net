# HOCON 

HOCON (Human-Optimized Config Object Notation) es un formato flexible y extensible de configuracion.

En Akka.NET permite configurar todo desde la implementación de un actor, como se hace el log, la comunicación de red a travez del `IActorRefProvider` y, más comúnmente, **cómo se implementan los actores individuales**.

Los valores devueltos por HOCON son fuertemente tipados

## Uso habitual

HOCON se usa comúnmente para ajustar la configuración de log, habilitar módulos especiales (como `Akka.Remote`), o configurar implementaciones como el `Dispatcher` o `Router` para un actor en particular.

Un ejemplo de uso seria:

```csharp
var config = ConfigurationFactory.ParseString(@"
akka.remote.dot-netty.tcp {
    transport-class = ""Akka.Remote.Transport.DotNetty.DotNettyTransport, Akka.Remote""
    transport-protocol = tcp
    port = 8091
    hostname = ""127.0.0.1""
}");

var system = ActorSystem.Create("MyActorSystem", config);

```

### Podemos usar HOCON dentro de un xml (como el Web.Config)

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section name="akka" type="Akka.Configuration.Hocon.AkkaConfigurationSection, Akka" />
  </configSections>

  <akka>
    <hocon>
      <![CDATA[
          akka {
            # here we are configuring log levels
            log-config-on-start = off
            stdout-loglevel = INFO
            loglevel = ERROR
            # this config section will be referenced as akka.actor
            actor {
              provider = remote
              debug {
                  receive = on
                  autoreceive = on
                  lifecycle = on
                  event-stream = on
                  unhandled = on
              }
            }
            # here we're configuring the Akka.Remote module
            remote {
              dot-netty.tcp {
                  transport-class = "Akka.Remote.Transport.DotNetty.DotNettyTransport, Akka.Remote"
                  #applied-adapters = []
                  transport-protocol = tcp
                  port = 8091
                  hostname = "127.0.0.1"
              }
            log-remote-lifecycle-events = INFO
          }
      ]]>
    </hocon>
  </akka>
</configuration>
```

y lo usamos asi:

```csharp
var system = ActorSystem.Create("MySystem"); //se carga la configuracion automaticamente del web.config
```

---

Ejemplos de configuraciones: https://getakka.net/articles/configuration/akka.html