```csharp 
    public class Program
    {
        public static ActorSystem MyActorSystem;
        static void Main(string[] args)
        {
            MyActorSystem = ActorSystem.Create("MyActorSystem");

            IActorRef pepita = MyActorSystem.ActorOf<Pepita>("pepita");
        }

        public class Pepita : ReceiveActor
        {
            private int _energiaDisponible;

            public Pepita()
            {
                _energiaDisponible = 100;
            }

            protected override void PostRestart(Exception reason)
            {
                base.PostRestart(reason);
            }

            protected override void PostStop()
            {
                base.PostStop();
            }

            protected override void PreRestart(Exception reason, object message)
            {
                base.PreRestart(reason, message);
            }

            protected override void PreStart()
            {
                base.PreStart();
            }
        }

 ```
