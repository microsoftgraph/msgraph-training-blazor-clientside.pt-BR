---
ms.openlocfilehash: c9fb7269969b0ef4e0300b8884c3ed168216b6cc
ms.sourcegitcommit: ef990e983274cb161bfe16a8dff801d30a798f04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2021
ms.locfileid: "53446960"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="36de8-101">Neste exercício, você criará um novo registro de aplicativo Web do Azure AD usando o Azure Active Directory de administração.</span><span class="sxs-lookup"><span data-stu-id="36de8-101">In this exercise, you will create a new Azure AD web application registration using the Azure Active Directory admin center.</span></span>

1. <span data-ttu-id="36de8-102">Abra um navegador e navegue até o [centro de administração do Azure Active Directory](https://aad.portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="36de8-102">Open a browser and navigate to the [Azure Active Directory admin center](https://aad.portal.azure.com).</span></span> <span data-ttu-id="36de8-103">Faça logon usando uma **conta pessoal** (também conhecida como Conta da Microsoft) ou **Conta Corporativa ou de Estudante**.</span><span class="sxs-lookup"><span data-stu-id="36de8-103">Login using a **personal account** (aka: Microsoft Account) or **Work or School Account**.</span></span>

1. <span data-ttu-id="36de8-104">Selecione **Azure Active Directory** na navegação esquerda e selecione **Registros de aplicativos** em **Gerenciar**.</span><span class="sxs-lookup"><span data-stu-id="36de8-104">Select **Azure Active Directory** in the left-hand navigation, then select **App registrations** under **Manage**.</span></span>

    ![<span data-ttu-id="36de8-105">Uma captura de tela dos registros do aplicativo</span><span class="sxs-lookup"><span data-stu-id="36de8-105">A screenshot of the App registrations</span></span> ](./images/aad-portal-app-registrations.png)

1. <span data-ttu-id="36de8-106">Selecione **Novo registro**.</span><span class="sxs-lookup"><span data-stu-id="36de8-106">Select **New registration**.</span></span> <span data-ttu-id="36de8-107">Na página **Registrar um aplicativo**, defina os valores da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="36de8-107">On the **Register an application** page, set the values as follows.</span></span>

    - <span data-ttu-id="36de8-108">Defina **Nome** para `Blazor Graph Tutorial`.</span><span class="sxs-lookup"><span data-stu-id="36de8-108">Set **Name** to `Blazor Graph Tutorial`.</span></span>
    - <span data-ttu-id="36de8-109">Defina **Tipos de conta com suporte** para **Contas em qualquer diretório organizacional e contas pessoais da Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="36de8-109">Set **Supported account types** to **Accounts in any organizational directory and personal Microsoft accounts**.</span></span>
    - <span data-ttu-id="36de8-110">Em **URI de** redirecionamento, de definir o primeiro **drop-down** como SPA (aplicativo de página única) e definir o valor como `https://localhost:5001/authentication/login-callback` .</span><span class="sxs-lookup"><span data-stu-id="36de8-110">Under **Redirect URI**, set the first drop-down to **Single-page application (SPA)** and set the value to `https://localhost:5001/authentication/login-callback`.</span></span>

    ![Captura de tela da página Registrar um aplicativo](./images/aad-register-an-app.png)

1. <span data-ttu-id="36de8-112">Selecione **Registrar**.</span><span class="sxs-lookup"><span data-stu-id="36de8-112">Select **Register**.</span></span> <span data-ttu-id="36de8-113">Na página **Tutorial Graph Blazor,** copie o valor da ID do Aplicativo **(cliente)** e salve-a, você precisará dela na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="36de8-113">On the **Blazor Graph Tutorial** page, copy the value of the **Application (client) ID** and save it, you will need it in the next step.</span></span>

    ![Captura de tela da ID do aplicativo do novo registro do aplicativo](./images/aad-application-id.png)
