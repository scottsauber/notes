### High Signal to Noise Ratio - Chekhov's Gun

Anton Chekhov was a Russian playwright, and he argued everything in a story must be relevant. If a gun is hanging on a wall, then it must be fired later in the story, otherwise it shouldn't be hanging there.

In the arrange phase of setting up your test, remove all extra noise. Change JUST the bit that is relevant to the test.

Instead of this:

```csharp
[Fact]
public void ShouldReturnErrorsForFirstNameWhenFirstNameIsNull()
{
   var customer = new Customer
   {
       Address = "123 1st Street",
       FirstName = null,
       MiddleName = "Bob",
       LastName = "Smith",
   };

   var result = _customerValidator.Validate(customer);

   result.Errors.Count.Should().Be(1);
   result.Errors[0].Should().Be("First Name is required.");
}
```

Do this:

```csharp
[Fact]
public void ShouldReturnErrorsForFirstNameWhenFirstNameIsNull()
{
   var customer = CreateValidCustomer();
   customer.FirstName = null;

   var result = _customerValidator.Validate(customer);

   result.Errors.Count.Should().Be(1);
   result.Errors[0].Should().Be("First Name is required.");
}
```

Setting up the customer's Address, MiddleName, and LastName is not relevant to the test, so it just adds noise. The second test is much more clear about what's actually being tested here.

### Analogy

An analogy to testing is Debits and Credits. Accountants use this to help double check their work. Both tests and debits/credits aren't perfect, but they help find issues. Both are production.

### Mock all the things vs integration test all the things

Mocking is a tradeoff.  You can get better defect localization, but it may come at the cost of reduced confidence and less ability to refactor (if your tests are implementation aware) without using other practices such as reconnect. Integration tests on the other hand, come at the cost of higher maintenance and less defect localization, but higher confidence and potentially more ability to refactor.  I don't openly choose which one is "best," the context around me helps inform which of these tradeoffs I'm willing to accept.
