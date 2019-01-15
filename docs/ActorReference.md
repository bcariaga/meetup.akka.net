
Un actor es un contenedor para:
 + Estado.
 + Comportamiento. 
 + Buzón.
 + Hijos.
 + Estrategia de Supervisión. 
 
Todo esto está encapsulado dentro de una referencia de actor. Un aspecto notable es que los actores tienen un ciclo de vida explícito, no se destruyen automáticamente cuando ya no son referenciados; después de haber creado uno, es su responsabilidad asegurarse de que también terminará, lo que también le da control sobre cómo se liberan los recursos cuando termina un actor.

 ![actores](https://getakka.net/images/actor.png)

```csharp 
    public class Program
    {
        public static ActorSystem MyActorSystem;
        
        static void Main(string[] args)
        {
            MyActorSystem = ActorSystem.Create("MyActorSystem");

            IActorRef pepita1 = MyActorSystem.ActorOf<Pepita>("pepita");
            IActorRef pepita2 = MyActorSystem.ActorOf<Pepita>("pepita");
        }

        public class Pepita : ReceiveActor
        {

        }
    }

 ```
