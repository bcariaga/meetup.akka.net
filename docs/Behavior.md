```csharp 
public class MyActor: ReceiveActor
{
  public MyActor()
  {
    Receive<string>(message => {
      //Hacer algo
    });
    Receive<Clase1>(message => {...});
    Receive<Clase3>(message => {...});
    Receive<Clase4>(message => {...});
  }
}

 ```
