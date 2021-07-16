---
ms.openlocfilehash: 25caea9275c57faa9c741e274ac90606959422c2
ms.sourcegitcommit: ef990e983274cb161bfe16a8dff801d30a798f04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2021
ms.locfileid: "53446981"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="8d2b4-101">Este tutorial ensina como criar um aplicativo Blazor WebAssembly do lado do cliente que usa a API do Microsoft Graph para recuperar informações de calendário para um usuário.</span><span class="sxs-lookup"><span data-stu-id="8d2b4-101">This tutorial teaches you how to build a client-side Blazor WebAssembly app that uses the Microsoft Graph API to retrieve calendar information for a user.</span></span>

> [!TIP]
> <span data-ttu-id="8d2b4-102">Se você preferir apenas baixar o tutorial concluído, você pode baixar ou clonar o [GitHub repositório](https://github.com/microsoftgraph/msgraph-training-blazor-clientside).</span><span class="sxs-lookup"><span data-stu-id="8d2b4-102">If you prefer to just download the completed tutorial, you can download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-blazor-clientside).</span></span> <span data-ttu-id="8d2b4-103">Consulte o arquivo README na pasta **de demonstração** para obter instruções sobre como configurar o aplicativo com uma ID do aplicativo e segredo.</span><span class="sxs-lookup"><span data-stu-id="8d2b4-103">See the README file in the **demo** folder for instructions on configuring the app with an app ID and secret.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d2b4-104">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8d2b4-104">Prerequisites</span></span>

<span data-ttu-id="8d2b4-105">Antes de iniciar este tutorial, você deve ter o [SDK do .NET Core](https://dotnet.microsoft.com/download) instalado em sua máquina de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8d2b4-105">Before you start this tutorial, you should have the [.NET Core SDK](https://dotnet.microsoft.com/download) installed on your development machine.</span></span> <span data-ttu-id="8d2b4-106">Se você não tiver o SDK, visite o link anterior para opções de download.</span><span class="sxs-lookup"><span data-stu-id="8d2b4-106">If you do not have the SDK, visit the previous link for download options.</span></span>

<span data-ttu-id="8d2b4-107">Você também deve ter uma conta pessoal da Microsoft com uma caixa de correio em Outlook.com, ou uma conta de trabalho ou de estudante da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8d2b4-107">You should also have either a personal Microsoft account with a mailbox on Outlook.com, or a Microsoft work or school account.</span></span> <span data-ttu-id="8d2b4-108">Se você não tiver uma conta da Microsoft, há algumas opções para obter uma conta gratuita:</span><span class="sxs-lookup"><span data-stu-id="8d2b4-108">If you don't have a Microsoft account, there are a couple of options to get a free account:</span></span>

- <span data-ttu-id="8d2b4-109">Você pode [se inscrever em uma nova conta pessoal da Microsoft.](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=12&ct=1454618383&rver=6.4.6456.0&wp=MBI_SSL_SHARED&wreply=https://mail.live.com/default.aspx&id=64855&cbcxt=mai&bk=1454618383&uiflavor=web&uaid=b213a65b4fdc484382b6622b3ecaa547&mkt=E-US&lc=1033&lic=1)</span><span class="sxs-lookup"><span data-stu-id="8d2b4-109">You can [sign up for a new personal Microsoft account](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=12&ct=1454618383&rver=6.4.6456.0&wp=MBI_SSL_SHARED&wreply=https://mail.live.com/default.aspx&id=64855&cbcxt=mai&bk=1454618383&uiflavor=web&uaid=b213a65b4fdc484382b6622b3ecaa547&mkt=E-US&lc=1033&lic=1).</span></span>
- <span data-ttu-id="8d2b4-110">Você pode [se inscrever no programa Office 365 desenvolvedor para](https://developer.microsoft.com/office/dev-program) obter uma assinatura Office 365 gratuita.</span><span class="sxs-lookup"><span data-stu-id="8d2b4-110">You can [sign up for the Office 365 Developer Program](https://developer.microsoft.com/office/dev-program) to get a free Office 365 subscription.</span></span>

> [!NOTE]
> <span data-ttu-id="8d2b4-111">Este tutorial foi escrito com o .NET Core SDK versão 5.0.302.</span><span class="sxs-lookup"><span data-stu-id="8d2b4-111">This tutorial was written with .NET Core SDK version 5.0.302.</span></span> <span data-ttu-id="8d2b4-112">As etapas neste guia podem funcionar com outras versões, mas que não foram testadas.</span><span class="sxs-lookup"><span data-stu-id="8d2b4-112">The steps in this guide may work with other versions, but that has not been tested.</span></span>

## <a name="feedback"></a><span data-ttu-id="8d2b4-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d2b4-113">Feedback</span></span>

<span data-ttu-id="8d2b4-114">Forneça qualquer comentário sobre este tutorial no [repositório GitHub .](https://github.com/microsoftgraph/msgraph-training-blazor-clientside)</span><span class="sxs-lookup"><span data-stu-id="8d2b4-114">Please provide any feedback on this tutorial in the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-blazor-clientside).</span></span>
