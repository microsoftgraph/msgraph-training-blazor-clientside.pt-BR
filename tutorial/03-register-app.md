---
ms.openlocfilehash: c9fb7269969b0ef4e0300b8884c3ed168216b6cc
ms.sourcegitcommit: ef990e983274cb161bfe16a8dff801d30a798f04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2021
ms.locfileid: "53446960"
---
<!-- markdownlint-disable MD002 MD041 -->

Neste exercício, você criará um novo registro de aplicativo Web do Azure AD usando o Azure Active Directory de administração.

1. Abra um navegador e navegue até o [centro de administração do Azure Active Directory](https://aad.portal.azure.com). Faça logon usando uma **conta pessoal** (também conhecida como Conta da Microsoft) ou **Conta Corporativa ou de Estudante**.

1. Selecione **Azure Active Directory** na navegação esquerda e selecione **Registros de aplicativos** em **Gerenciar**.

    ![Uma captura de tela dos registros do aplicativo ](./images/aad-portal-app-registrations.png)

1. Selecione **Novo registro**. Na página **Registrar um aplicativo**, defina os valores da seguinte forma.

    - Defina **Nome** para `Blazor Graph Tutorial`.
    - Defina **Tipos de conta com suporte** para **Contas em qualquer diretório organizacional e contas pessoais da Microsoft**.
    - Em **URI de** redirecionamento, de definir o primeiro **drop-down** como SPA (aplicativo de página única) e definir o valor como `https://localhost:5001/authentication/login-callback` .

    ![Captura de tela da página Registrar um aplicativo](./images/aad-register-an-app.png)

1. Selecione **Registrar**. Na página **Tutorial Graph Blazor,** copie o valor da ID do Aplicativo **(cliente)** e salve-a, você precisará dela na próxima etapa.

    ![Captura de tela da ID do aplicativo do novo registro do aplicativo](./images/aad-application-id.png)
