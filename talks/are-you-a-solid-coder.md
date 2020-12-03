Talk: https://www.infoq.com/presentations/solid-principles/

# Single Responsibility Principle

What's wrong with this interface?
```csharp
public interface IModem
{
    bool Dial(string number);
    void Hangup();
    void SendData(char data);
    char Receive();
}
```

### Violates SRP by dealing with connections and transferring data.  Instead:

```csharp
public interface IModemConnection
{
    bool Dial(string number);
    void Hangup();
}
public interface IModelChannel
{
    void SendData(char data);
    char Receive();
}
```

You could apply this same concept to a class that connects to a DB and retrieves data from that DB (.NET does this with `IDbConnection` and `DataReader`)