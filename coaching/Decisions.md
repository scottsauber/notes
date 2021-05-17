I like to categorize decisions by asking the question "What is the likelihood my app will fail if I make the wrong decision here?"

> When I use the word "fail" here, I mean from the standpoint of both the app being able to deliver business value now and in the future

For instance - choosing xUnit vs NUnit is an argument I hear people get into in .NET. It's pointless. Your app will not fail if you choose xUnit or NUnit. Moreover, it's probably less than 2 hours work to convert even a large test suite from one to the other if you change your mind. However, choosing the wrong language, architecture, cloud, etc. will absolutely cause your app to fail and changing your mind.

Alternatively, you can think of it as "is this decision a one-way door?" Choosing a language, is a one-way door. If it's not a one-way door, how quickly can I go through a different door?
