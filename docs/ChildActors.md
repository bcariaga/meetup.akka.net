Cada actor es potencialmente un supervisor: si crea hijos para delegar subtareas, los supervisará automáticamente. La lista de hijos se mantiene dentro del contexto del actor y el actor tiene acceso a ella. Las modificaciones a la lista se realizan creando hijos (Context.ActorOf (...)) o deteniendo (Context.Stop (hijo)) y estas acciones se reflejan de inmediato. Las acciones reales de creación y terminación ocurren de manera asíncrona detrás de escena, por lo que no "bloquean" a su supervisor.

```csharp 
    public class Program
    {
        public static ActorSystem MyActorSystem;
        static void Main(string[] args)
        {
            MyActorSystem = ActorSystem.Create("MyActorSystem");

            IActorRef pepita = MyActorSystem.ActorOf<Pepita>("pepita");

            pepita.Tell(new Saludar { Mensaje = "hola pepita hija!!" });

            MyActorSystem.WhenTerminated.Wait();
        }

        public class Pepita : ReceiveActor
        {
            private int _energiaDisponible = 100;
            IActorRef pepitaHija;

            public Pepita()
            {
                Receive<Saludar>(saludo => pepitaHija.Tell(saludo));
                Receive<Responder>(respuesta => Console.WriteLine(respuesta));
            }

            protected override void PreStart()
            {
                Context.ActorOf<PepitaHija>("pepitaHija");
                base.PreStart();
            }
        }
        public class PepitaHija : ReceiveActor
        {
            public PepitaHija()
            {
                Receive<Saludar>(msg =>
                    Sender.Tell(new Responder
                    {
                        Mensaje = "saludo recibido!!"
                    }));
            }
        }

        public class Saludar { public string Mensaje { get; set; } }
        public class Responder { public string Mensaje { get; set; } }
    }

 ```
