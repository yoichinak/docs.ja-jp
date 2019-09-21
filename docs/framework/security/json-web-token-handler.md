---
title: JSON Web トークン ハンドラー
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 3dc76f3de714fd91d397cc240d02a1a8605fe18b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045330"
---
# <a name="json-web-token-handler"></a>JSON Web トークン ハンドラー
Windows Identity Foundation の JSON Web トークン ハンドラー拡張機能を使用すると、アプリケーションで JSON Web トークン (JWT) を作成して検証できます。 JWT トークン ハンドラーは、他の組み込みセキュリティ トークン ハンドラーのような WIF パイプラインで実行されるように構成できますが、別個に使用して軽量のアプリケーションでトークン検証を実行することもできます。 Microsoft Azure Active Directory での認証など、OAuth 2.0 ベアラー トークン スキームを使用している場合は、JWT トークン ハンドラーが特に役立ちます。  
  
 JWT トークン ハンドラーは、NuGet パッケージとして入手できます。 詳細については、「[JSON Web トークン ハンドラー パッケージのダウンロード](downloading-the-json-web-token-handler-package.md)」を参照してください。  
  
## <a name="scenarios"></a>シナリオ  
 JWT トークン ハンドラーにより、次の主要なシナリオが可能になります。  
  
- **サーバーアプリケーションで JWT トークンを検証する**:このシナリオでは、Litware という会社が、WIF を使用して web サインオン要求を処理するサーバーアプリケーションを持っています。 Litware は、アプリケーションが認証に JWT トークンを使用できるようにしたいと思っています。 このアプリケーションが JWT トークン ハンドラーで更新された後、アプリケーション構成が更新されて、WIF パイプラインに JWT トークン ハンドラーが追加されます。 更新が行われてから新しい要求が WIF パイプラインに入ると、新しいハンドラーを使用して JWT トークンが検証され、正常な認証が行われます。  
  
- **REST Web サービスで JWT トークンを検証し**ます。このシナリオでは、Litware という会社が Windows Azure Active Directory によって保護された REST web サービスを持っています。 Web サービスへの要求は、正常な認証時 JWT トークンを発行する Microsoft Azure AD により認証する必要があります。 Litware には、Web サービスへのアクセスが必要なクライアント アプリケーションがあります。 このクライアントが Web サービスに要求を行い、Microsoft Azure AD から取得した JWT トークンを提示した後、Web サービスにより JWT トークン ハンドラーを使用してトークンが検証されます。 JWT トークン ハンドラーがトークンを検証した後、Web サービスによって目的のリソースがクライアントに返されます。  
  
## <a name="features"></a>機能  
 JWT トークン ハンドラーには、次の機能が備わっています。  
  
- **JWT トークンを検証する**:JWT トークンは、アプリケーションの WIF パイプラインの一部として、または WIF とは別に呼び出されたトークンハンドラーの検証ロジックによって簡単に検証できます。  
  
- **JWT トークンを作成し**ます。JWT トークンハンドラーを使用して、ダウンストリームサービスで承認のための JWT トークンを作成することができます。
