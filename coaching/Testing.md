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
