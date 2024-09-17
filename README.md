# Desenvolvimento de APIs em `C#`

Neste guia, você aprenderá a criar uma API mínima em C# usando o .NET 6. A API será um sistema bancário simples chamado QBankApi, que permitirá a criação, leitura, atualização e exclusão de contas bancárias.

## Pré-requisitos

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [Visual Studio Code](https://code.visualstudio.com/)
- [C# for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)
- [REST Client for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=humao.rest-client)
- [Thunder Client for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client)

## O Projeto

O sistema permite que os clientes do banco realizem diversas operações bancárias por meio do Aplicativo. Inclui gerenciamento de contas, transações para fazer transferências, solicitação e gerenciamento de empréstimos, gerenciamento de cartões de crédito e pagamentos de serviços externos, como universidades e telefonia.

A conta do cliente permitirá o acesso a todas essas operações.

## Estrutura Modular

1. Módulo de Contas: Aqui o usuário terá a opção de criar contas, visualizá-las, atualizá-las e excluí-las.

2. Módulo de transações: Uma vez criada a conta, o usuário poderá realizar diversas transações, como transferências para contas próprias, transferências para terceiros e transferências para outros bancos.

3. Módulo Empréstimo: Neste módulo o usuário pode solicitar um empréstimo anexando todas as informações necessárias e preenchendo o formulário correspondente. O sistema calculará o valor que o usuário poderá emprestar e o plano de pagamento. Além disso, você pode efetuar o pagamento mensal de suas parcelas ou agendá-las caso queira o débito automático.

4. Módulo Cartão de Crédito: Neste módulo o usuário pode solicitar seu cartão de crédito preenchendo o formulário de inscrição. O sistema calculará o limite de crédito que o usuário poderá acessar. Assim que o cartão for aprovado, o usuário poderá realizar compras e também terá a opção de pagar manualmente a dívida ou agendar pagamentos caso queira o débito automático.

5. Módulo de Pagamento de Serviços: Este módulo permitirá ao usuário efetuar pagamentos de serviços externos, como mensalidades universitárias, despesas de gerais ou serviços telefônicos, entre outros. Para tal, o utilizador deverá registar o serviço ao qual pretende efetuar o pagamento, fornecendo os dados necessários, podendo efetuar pagamentos manuais ou agendá-los caso prefira o débito automático.

## Passos para criar a API mínima

### Passo 1: Criar um novo projeto Web API

Primeiro, vamos criar um novo projeto de API mínima usando o .NET CLI:

```bash
dotnet new web -o QBankApi
cd .\QBankApi\
```

Abra o projeto no Visual Studio Code:

```bash
code .
```

No arquivo `Program.cs`, adicione o seguinte código para configurar a API mínima:

```csharp
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/", () => "Hello World!");

app.Run();
```

### Passo 2: Executar a API

Execute a API usando o comando:

```bash
dotnet run
```

Você verá as seguintes informações no console:

```plaintext
info: Microsoft.Hosting.Lifetime[14]
      Now listening on: http://localhost:5013
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: F:\source\Repos\sistemas_distribuidos\ApiAula1
```

A API estará disponível em `http://localhost:5013`.

### Passo 3: Criar uma pasta para os Objetos de Negócio (DTOs)

Vamos criar uma pasta para os Objetos de Transferência de Dados (DTOs). Os DTOs são usados para transferir dados entre diferentes camadas da aplicação.

1. Crie uma pasta chamada `DTOs` no diretório raiz do projeto.
2. Dentro da pasta `DTOs`, crie um arquivo chamado `AccountDTO.cs` com o seguinte conteúdo:

```csharp
namespace QBankApi.DTOs
{
    public class AccountDTO
    {
        public int Id { get; set; }
        public string AccountNumber { get; set; }
        public string AccountHolder { get; set; }
        public decimal Balance { get; set; }
    }
}
```

### Passo 4: Criar uma pasta para os Modelos (Models)

Vamos criar uma pasta para os Modelos. Os Modelos representam as entidades do domínio do sistema bancário.

1. Crie uma pasta chamada `Models` no diretório raiz do projeto.
2. Dentro da pasta `Models`, crie um arquivo chamado `Account.cs` com o seguinte conteúdo:

```csharp
namespace QBankApi.Models
{
    public class Account
    {
        public int Id { get; set; }
        public string AccountNumber { get; set; }
        public string AccountHolder { get; set; }
        public decimal Balance { get; set; }
    }
}
```

### Passo 5: Criar rotas para fazer o CRUD via REST

Agora, vamos criar rotas para realizar operações CRUD (Create, Read, Update, Delete) na classe representada pelos Models.

1. No arquivo `Program.cs`, adicione as seguintes rotas:

```csharp
app.MapGet("/accounts", () =>
{
    // Código para obter todas as contas
});

app.MapGet("/accounts/{id}", (int id) =>
{
    // Código para obter uma conta por ID
});

app.MapPost("/accounts", (Account account) =>
{
    // Código para criar uma nova conta
});

app.MapPut("/accounts/{id}", (int id, Account updatedAccount) =>
{
    // Código para atualizar uma conta existente
});

app.MapDelete("/accounts/{id}", (int id) =>
{
    // Código para deletar uma conta
});
```

### Conclusão

Com esses passos, você criou a estrutura inicial da API do QBankApi em C#. A API mínima está configurada e pronta para ser expandida com mais funcionalidades, como gerenciamento de contas, transações, empréstimos, cartões de crédito e pagamentos de serviços. Continue desenvolvendo o projeto seguindo a teoria incremental e aplicando as técnicas aprendidas. Boa sorte! 🚀

## Referências

- [ASP.NET Core Web API](https://docs.microsoft.com/pt-br/aspnet/core/web-api/?view=aspnetcore-5.0)
- [Tutorial: Criar uma API Web com ASP.NET Core](https://learn.microsoft.com/pt-br/aspnet/core/tutorials/first-web-api?view=aspnetcore-8.0&preserve-view=true&tabs=visual-studio)

## Autor

- [Professor Alexandre Montanha](https://www.linkedin.com/in/professor-montanha/)
- [GitHub](https://github.com/alexmontanha)
