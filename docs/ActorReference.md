
```csharp 
public class MyActor: ReceiveActor
{
  private readonly ILoggingAdapter log = Context.GetLogger();

  public MyActor()
  {
    Receive<string>(message => {
      log.Info("Received String message: {0}", message);
      Sender.Tell(message);
    });
    Receive<SomeMessage>(message => {...});
  }
}

 ```

 ![actores](https://getakka.net/images/actor.png)
