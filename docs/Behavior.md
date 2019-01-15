```csharp 
    public class Program
    {
        public static ActorSystem MyActorSystem;
        static void Main(string[] args)
        {
            MyActorSystem = ActorSystem.Create("MyActorSystem");

            IActorRef pepita = MyActorSystem.ActorOf<Pepita>("pepita");

            pepita.Tell("volar");
            pepita.Tell("comer");

            MyActorSystem.WhenTerminated.Wait();
        }

        public class Pepita : ReceiveActor
        {
            private int _energiaDisponible = 100;

            public Pepita()
            {
                Become(Volar);
            }

            private void Comer()
            {
                Receive<string>(mensaje => mensaje == "comer", mensaje =>
                {
                    _energiaDisponible += 10;
                    Become(Volar);
                });
            }

            private void Volar()
            {
                Receive<string>(mensaje => mensaje == "volar", mensaje =>
                {
                    _energiaDisponible -= 10;
                    Become(Comer);
                });
            }

            protected override void PreStart()
            {
                //Generalmente se usa para inicializar los hijos acá
                base.PreStart();
            }
        }
    }

 ```
