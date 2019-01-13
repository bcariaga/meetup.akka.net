# Remoting

Akka es una libreria extensible, el paquete base brinda todo lo necesario para trabajar con akka, pero hayo docenas de modulos adicionales que agregan nuevas funciones.

**Akka.Remote** es el más poderoso de todos estos paquetes adicionales, ya que es lo que brinda la capacidad de **construir un ActorSystem a través de múltiples procesos en una red de computadoras**.

De esta manera podemos conectar actores a través de una red.

## Capacidades de Akka.Remote 

Akka.Remote brinda:

+ Transparencia de ubicación con RemoteActorRef: escriba código que parece que se está comunicando con actores locales, pero con solo unos pocos ajustes de configuración, sus actores pueden comenzar a comunicarse con actores alojados en procesos remotos de una manera que sea completamente transparente a su código. 
+ Direccionamiento remoto: Akka.Remote extiende los componentes `Address` y `ActorPath` de Akka.NET para incluir ahora también información sobre cómo conectarse a procesos remotos a través de `ActorSelection`. 
+ Mensajería remota: envíe mensajes, de manera transparente, a los actores que se ejecutan en `ActorSystems` remotos en otros lugares de la red. 
+ **Implementación remota**: implemente de forma remota actores a través del método `ActorOf` en instancias remotas de `ActorSystem`, ¡en cualquier lugar de la red! La ubicación de sus actores en la red se convierte en un detalle de implementación en Akka.Remote. 
+ Múltiples transportes de red: listos para usar Akka.Remote se envía con soporte para TCP, pero tiene la Capacidad de conectar transportes de terceros y activar varios de ellos al mismo tiempo.

La mayoría de la configuración de Akka.Remote se hace, valga la redundancia, a través de la configuración, y no necesariamente con código, de manera que se pueda implementar fácilmente sin tener que hacer _"deploy"_

El funcionamiento del sistema pasa a ser "_Peer-to-Peer_"