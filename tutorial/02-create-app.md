---
ms.openlocfilehash: 4c021fe8aac9b42ee0984a15e73366ead847ee06
ms.sourcegitcommit: ef990e983274cb161bfe16a8dff801d30a798f04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2021
ms.locfileid: "53446974"
---
<!-- markdownlint-disable MD002 MD041 -->

Comece criando um aplicativo Blazor WebAssembly.

1. Abra sua interface de linha de comando (CLI) em um diretório onde você deseja criar o projeto. Execute o seguinte comando:

    ```Shell
    dotnet new blazorwasm --auth SingleOrg -o GraphTutorial
    ```

    O `--auth SingleOrg` parâmetro faz com que o projeto gerado inclua a configuração para autenticação com o plataforma de identidade da Microsoft.

1. Depois que o projeto for criado, verifique se ele funciona alterando o diretório atual para o diretório **GraphTutorial** e executando o seguinte comando em sua CLI.

    ```Shell
    dotnet watch run
    ```

1. Abra seu navegador e navegue até `https://localhost:5001` . Se tudo estiver funcionando, você deverá ver um "Olá, mundo!" Mensagem.

> [!IMPORTANT]
> Se você receber um aviso de que o certificado para **localhost** não é confiável, você pode usar a CLI do .NET Core para instalar e confiar no certificado de desenvolvimento. Consulte [Enforce HTTPS in ASP.NET Core](/aspnet/core/security/enforcing-ssl) para obter instruções para sistemas operacionais específicos.

## <a name="add-nuget-packages"></a>Adicionar pacotes NuGet

Antes de continuar, instale alguns pacotes NuGet que você usará posteriormente.

- [Microsoft.Graph](https://www.nuget.org/packages/Microsoft.Graph/) para fazer chamadas para o Microsoft Graph.
- [TimeZoneConverter para](https://github.com/mj1856/TimeZoneConverter) traduzir Windows de fuso horário para identificadores IANA.

1. Execute os seguintes comandos em sua CLI para instalar as dependências.

    ```Shell
    dotnet add package Microsoft.Graph --version 4.0.0
    dotnet add package TimeZoneConverter
    ```

## <a name="design-the-app"></a>Design do aplicativo

Nesta seção, você criará a estrutura básica da interface do usuário do aplicativo.

1. Remova páginas de exemplo geradas pelo modelo. Exclua os arquivos a seguir.

    - **./Pages/Counter.razor**
    - **./Pages/FetchData.razor**
    - **./Shared/SurveyPrompt.razor**
    - **./wwwroot/sample-data/weather.json**

1. Abra **./wwwroot/index.html** e adicione o código a seguir logo **antes da** marca de `</body>` fechamento.

    :::code language="html" source="../demo/GraphTutorial/wwwroot/index.html" id="BootStrapJSSnippet":::

    Isso adiciona os [arquivos javascript bootstrap.](https://getbootstrap.com/docs/4.5/getting-started/introduction/)

1. Abra **./wwwroot/css/app.css** e adicione o código a seguir.

    :::code language="css" source="../demo/GraphTutorial/wwwroot/css/app.css" id="CssSnippet":::

1. Abra **./Shared/NavMenu.razor** e substitua seu conteúdo pelo seguinte.

    :::code language="razor" source="../demo/GraphTutorial/Shared/NavMenu.razor" id="NavMenuSnippet":::

1. Abra **./Pages/Index.razor** e substitua seu conteúdo pelo seguinte.

    :::code language="razor" source="../demo/GraphTutorial/Pages/Index.razor" id="IndexSnippet":::

1. Abra **./Shared/LoginDisplay.razor** e substitua seu conteúdo pelo seguinte.

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

1. Crie um novo diretório no **diretório ./wwwroot** chamado **img**. Adicione um arquivo de imagem de sua escolha chamada **no-profile-photo.png** neste diretório. Essa imagem será usada como a foto do usuário quando o usuário não tiver nenhuma foto no Microsoft Graph.

    > [!TIP]
    > Você pode baixar a imagem usada nessas capturas de tela de [GitHub](https://github.com/microsoftgraph/msgraph-training-blazor-clientside/blob/master/demo/GraphTutorial/wwwroot/img/no-profile-photo.png).

1. Salve todas as alterações e atualize a página.

    ![Captura de tela da home page](./images/create-app-01.png)
