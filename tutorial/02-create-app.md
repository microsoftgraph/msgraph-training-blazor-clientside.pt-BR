---
ms.openlocfilehash: 4c021fe8aac9b42ee0984a15e73366ead847ee06
ms.sourcegitcommit: ef990e983274cb161bfe16a8dff801d30a798f04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2021
ms.locfileid: "53446974"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="1615c-101">Comece criando um aplicativo Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="1615c-101">Start by creating a Blazor WebAssembly app.</span></span>

1. <span data-ttu-id="1615c-102">Abra sua interface de linha de comando (CLI) em um diretório onde você deseja criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="1615c-102">Open your command-line interface (CLI) in a directory where you want to create the project.</span></span> <span data-ttu-id="1615c-103">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="1615c-103">Run the following command.</span></span>

    ```Shell
    dotnet new blazorwasm --auth SingleOrg -o GraphTutorial
    ```

    <span data-ttu-id="1615c-104">O `--auth SingleOrg` parâmetro faz com que o projeto gerado inclua a configuração para autenticação com o plataforma de identidade da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1615c-104">The `--auth SingleOrg` parameter causes the generated project to include configuration for authentication with the Microsoft identity platform.</span></span>

1. <span data-ttu-id="1615c-105">Depois que o projeto for criado, verifique se ele funciona alterando o diretório atual para o diretório **GraphTutorial** e executando o seguinte comando em sua CLI.</span><span class="sxs-lookup"><span data-stu-id="1615c-105">Once the project is created, verify that it works by changing the current directory to the **GraphTutorial** directory and running the following command in your CLI.</span></span>

    ```Shell
    dotnet watch run
    ```

1. <span data-ttu-id="1615c-106">Abra seu navegador e navegue até `https://localhost:5001` .</span><span class="sxs-lookup"><span data-stu-id="1615c-106">Open your browser and browse to `https://localhost:5001`.</span></span> <span data-ttu-id="1615c-107">Se tudo estiver funcionando, você deverá ver um "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="1615c-107">If everything is working, you should see a "Hello, world!"</span></span> <span data-ttu-id="1615c-108">Mensagem.</span><span class="sxs-lookup"><span data-stu-id="1615c-108">message.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1615c-109">Se você receber um aviso de que o certificado para **localhost** não é confiável, você pode usar a CLI do .NET Core para instalar e confiar no certificado de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1615c-109">If you receive a warning that the certificate for **localhost** is un-trusted you can use the .NET Core CLI to install and trust the development certificate.</span></span> <span data-ttu-id="1615c-110">Consulte [Enforce HTTPS in ASP.NET Core](/aspnet/core/security/enforcing-ssl) para obter instruções para sistemas operacionais específicos.</span><span class="sxs-lookup"><span data-stu-id="1615c-110">See [Enforce HTTPS in ASP.NET Core](/aspnet/core/security/enforcing-ssl) for instructions for specific operating systems.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="1615c-111">Adicionar pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="1615c-111">Add NuGet packages</span></span>

<span data-ttu-id="1615c-112">Antes de continuar, instale alguns pacotes NuGet que você usará posteriormente.</span><span class="sxs-lookup"><span data-stu-id="1615c-112">Before moving on, install some additional NuGet packages that you will use later.</span></span>

- <span data-ttu-id="1615c-113">[Microsoft.Graph](https://www.nuget.org/packages/Microsoft.Graph/) para fazer chamadas para o Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="1615c-113">[Microsoft.Graph](https://www.nuget.org/packages/Microsoft.Graph/) for making calls to Microsoft Graph.</span></span>
- <span data-ttu-id="1615c-114">[TimeZoneConverter para](https://github.com/mj1856/TimeZoneConverter) traduzir Windows de fuso horário para identificadores IANA.</span><span class="sxs-lookup"><span data-stu-id="1615c-114">[TimeZoneConverter](https://github.com/mj1856/TimeZoneConverter) for translating Windows time zone identifiers to IANA identifiers.</span></span>

1. <span data-ttu-id="1615c-115">Execute os seguintes comandos em sua CLI para instalar as dependências.</span><span class="sxs-lookup"><span data-stu-id="1615c-115">Run the following commands in your CLI to install the dependencies.</span></span>

    ```Shell
    dotnet add package Microsoft.Graph --version 4.0.0
    dotnet add package TimeZoneConverter
    ```

## <a name="design-the-app"></a><span data-ttu-id="1615c-116">Design do aplicativo</span><span class="sxs-lookup"><span data-stu-id="1615c-116">Design the app</span></span>

<span data-ttu-id="1615c-117">Nesta seção, você criará a estrutura básica da interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1615c-117">In this section you will create the basic UI structure of the application.</span></span>

1. <span data-ttu-id="1615c-118">Remova páginas de exemplo geradas pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="1615c-118">Remove sample pages generated by the template.</span></span> <span data-ttu-id="1615c-119">Exclua os arquivos a seguir.</span><span class="sxs-lookup"><span data-stu-id="1615c-119">Delete the following files.</span></span>

    - <span data-ttu-id="1615c-120">**./Pages/Counter.razor**</span><span class="sxs-lookup"><span data-stu-id="1615c-120">**./Pages/Counter.razor**</span></span>
    - <span data-ttu-id="1615c-121">**./Pages/FetchData.razor**</span><span class="sxs-lookup"><span data-stu-id="1615c-121">**./Pages/FetchData.razor**</span></span>
    - <span data-ttu-id="1615c-122">**./Shared/SurveyPrompt.razor**</span><span class="sxs-lookup"><span data-stu-id="1615c-122">**./Shared/SurveyPrompt.razor**</span></span>
    - <span data-ttu-id="1615c-123">**./wwwroot/sample-data/weather.json**</span><span class="sxs-lookup"><span data-stu-id="1615c-123">**./wwwroot/sample-data/weather.json**</span></span>

1. <span data-ttu-id="1615c-124">Abra **./wwwroot/index.html** e adicione o código a seguir logo **antes da** marca de `</body>` fechamento.</span><span class="sxs-lookup"><span data-stu-id="1615c-124">Open **./wwwroot/index.html** and add the following code just **before** the closing `</body>` tag.</span></span>

    :::code language="html" source="../demo/GraphTutorial/wwwroot/index.html" id="BootStrapJSSnippet":::

    <span data-ttu-id="1615c-125">Isso adiciona os [arquivos javascript bootstrap.](https://getbootstrap.com/docs/4.5/getting-started/introduction/)</span><span class="sxs-lookup"><span data-stu-id="1615c-125">This adds the [Bootstrap](https://getbootstrap.com/docs/4.5/getting-started/introduction/) javascript files.</span></span>

1. <span data-ttu-id="1615c-126">Abra **./wwwroot/css/app.css** e adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1615c-126">Open **./wwwroot/css/app.css** and add the following code.</span></span>

    :::code language="css" source="../demo/GraphTutorial/wwwroot/css/app.css" id="CssSnippet":::

1. <span data-ttu-id="1615c-127">Abra **./Shared/NavMenu.razor** e substitua seu conteúdo pelo seguinte.</span><span class="sxs-lookup"><span data-stu-id="1615c-127">Open **./Shared/NavMenu.razor** and replace its contents with the following.</span></span>

    :::code language="razor" source="../demo/GraphTutorial/Shared/NavMenu.razor" id="NavMenuSnippet":::

1. <span data-ttu-id="1615c-128">Abra **./Pages/Index.razor** e substitua seu conteúdo pelo seguinte.</span><span class="sxs-lookup"><span data-stu-id="1615c-128">Open **./Pages/Index.razor** and replace its contents with the following.</span></span>

    :::code language="razor" source="../demo/GraphTutorial/Pages/Index.razor" id="IndexSnippet":::

1. <span data-ttu-id="1615c-129">Abra **./Shared/LoginDisplay.razor** e substitua seu conteúdo pelo seguinte.</span><span class="sxs-lookup"><span data-stu-id="1615c-129">Open **./Shared/LoginDisplay.razor** and replace its contents with the following.</span></span>

    ```razor
    @using Microsoft.AspNetCore.Components.Authorization
    @using Microsoft.AspNetCore.Components.WebAssembly.Authentication

    @inject NavigationManager Navigation
    @inject SignOutSessionStateManager SignOutManager

    <AuthorizeView>
        <Authorized>
            <a class="text-decoration-none" data-toggle="dropdown" href="#" role="button">
                <img src="/img/no-profile-photo.png" class="nav-profile-photo rounded-circle align-self-center mr-2">
            </a>
            <div class="dropdown-menu dropdown-menu-right">
                <h5 class="dropdown-item-text mb-0">@context.User.Identity.Name</h5>
                <p class="dropdown-item-text text-muted mb-0">placeholder@contoso.com</p>
                <div class="dropdown-divider"></div>
                <button class="dropdown-item" @onclick="BeginLogout">Log out</button>
            </div>
        </Authorized>
        <NotAuthorized>
            <a href="authentication/login">Log in</a>
        </NotAuthorized>
    </AuthorizeView>

    @code{
        private async Task BeginLogout(MouseEventArgs args)
        {
            await SignOutManager.SetSignOutState();
            Navigation.NavigateTo("authentication/logout");
        }
    }
    ```

1. <span data-ttu-id="1615c-130">Crie um novo diretório no **diretório ./wwwroot** chamado **img**.</span><span class="sxs-lookup"><span data-stu-id="1615c-130">Create a new directory in the **./wwwroot** directory named **img**.</span></span> <span data-ttu-id="1615c-131">Adicione um arquivo de imagem de sua escolha chamada **no-profile-photo.png** neste diretório.</span><span class="sxs-lookup"><span data-stu-id="1615c-131">Add an image file of your choosing named **no-profile-photo.png** in this directory.</span></span> <span data-ttu-id="1615c-132">Essa imagem será usada como a foto do usuário quando o usuário não tiver nenhuma foto no Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="1615c-132">This image will be used as the user's photo when the user has no photo in Microsoft Graph.</span></span>

    > [!TIP]
    > <span data-ttu-id="1615c-133">Você pode baixar a imagem usada nessas capturas de tela de [GitHub](https://github.com/microsoftgraph/msgraph-training-blazor-clientside/blob/master/demo/GraphTutorial/wwwroot/img/no-profile-photo.png).</span><span class="sxs-lookup"><span data-stu-id="1615c-133">You can download the image used in these screenshots from [GitHub](https://github.com/microsoftgraph/msgraph-training-blazor-clientside/blob/master/demo/GraphTutorial/wwwroot/img/no-profile-photo.png).</span></span>

1. <span data-ttu-id="1615c-134">Salve todas as alterações e atualize a página.</span><span class="sxs-lookup"><span data-stu-id="1615c-134">Save all of your changes and refresh the page.</span></span>

    ![Captura de tela da home page](./images/create-app-01.png)
