# Welcome to our KYC Application

This is where you can start to get familiar with the codebase that we'll work with during our pairing session.
As you will see, it is focused on identifying code smells, refactoring and testing legacy codebase while promoting
conversations.

## Application description

In the world of banking, **KYC (Know Your Customer)** is the mandatory process of identifying and verifying the client's background when opening an account and periodically over time. In other words, banks must make sure that their clients are genuinely who they claim to be, and should refuse to open an account or halt a business relationship if the client fails to meet the minimum KYC requirements.   
To accomplish this, our application has a *KYCService* class that is responsible for performing the required checks against a customer.  

## Technology used

- C#
- .NET Core
- .NET Core CLI - build tool
- xUnit.net - unit testing framework

## Before the interview

Get familiar with the codebase! Make sure you have the necessary dependencies installed, and that you are able to run the tests.

## What you need to run it

- [.NET Core 6](https://dotnet.microsoft.com/en-us/download/dotnet/6.0)

## Build

```console
dotnet build
```

## Run Tests

```console
dotnet test
```

## Run the Application

To understand how this library would be used you can check the  `KYCSampleApp` class. If you want to see the results, run:

```console
dotnet run --project src/KYC/KYC.csproj
```

## Existing Business Rules

Our KYC check currently has the following rules:
- We compute a *risk score* based on customer's data, as follows:  
  - if the main address country is different than *Romania*, we increase the risk score by 20
  - if the customer's category is *Private* then we increase the risk score by 30 
  - for each reputation having module name *BL* and match rate greater than 0.4 we increase the risk score by 60
  - for each reputation having module name *SI* we increase the risk score by 100
- Finally we compute the final decision, whether the customer is acceptable or not:
  - if customer's type is *PF* and their final risk score is less than 50 then the customer is considered *acceptable*
  - if the customer's type is *PJ* and their final risk score is less or equal than 50 then the customer is considered *acceptable*
