---
title: JSON Web トークン ハンドラー
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 27c01a3d0ce0f2891b00ad28526d4753b9be4ce0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790131"
---
# <a name="json-web-token-handler"></a>JSON Web トークン ハンドラー
Windows Identity Foundation の JSON Web トークン ハンドラー拡張機能を使用すると、アプリケーションで JSON Web トークン (JWT) を作成して検証できます。 JWT トークン ハンドラーは、他の組み込みセキュリティ トークン ハンドラーのような WIF パイプラインで実行されるように構成できますが、別個に使用して軽量のアプリケーションでトークン検証を実行することもできます。 Microsoft Azure Active Directory での認証など、OAuth 2.0 ベアラー トークン スキームを使用している場合は、JWT トークン ハンドラーが特に役立ちます。  
  
 JWT トークン ハンドラーは、NuGet パッケージとして入手できます。 詳細については、「[JSON Web トークン ハンドラー パッケージのダウンロード](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md)」を参照してください。  
  
## <a name="scenarios"></a>シナリオ  
 JWT トークン ハンドラーにより、次の主要なシナリオが可能になります。  
  
- **サーバー アプリケーションで JWT トークンを検証**:このシナリオでは、Litware という会社は、web サインオン要求を処理するために WIF を使用するサーバー アプリケーションが。 Litware は、アプリケーションが認証に JWT トークンを使用できるようにしたいと思っています。 このアプリケーションが JWT トークン ハンドラーで更新された後、アプリケーション構成が更新されて、WIF パイプラインに JWT トークン ハンドラーが追加されます。 更新が行われてから新しい要求が WIF パイプラインに入ると、新しいハンドラーを使用して JWT トークンが検証され、正常な認証が行われます。  
  
- **REST Web サービスで JWT トークンを検証**:このシナリオでは、Litware という会社は、Windows Azure Active Directory によって保護された REST web サービスが。 Web サービスへの要求は、正常な認証時 JWT トークンを発行する Microsoft Azure AD により認証する必要があります。 Litware には、Web サービスへのアクセスが必要なクライアント アプリケーションがあります。 このクライアントが Web サービスに要求を行い、Microsoft Azure AD から取得した JWT トークンを提示した後、Web サービスにより JWT トークン ハンドラーを使用してトークンが検証されます。 JWT トークン ハンドラーがトークンを検証した後、Web サービスによって目的のリソースがクライアントに返されます。  
  
## <a name="features"></a>機能  
 JWT トークン ハンドラーには、次の機能が備わっています。  
  
- **JWT トークンを検証**:JWT トークンを簡単にするか、アプリケーションの WIF パイプラインの一部として、トークン ハンドラーの検証ロジックによって検証または WIF とは無関係に呼び出されます  
  
- **作成、JWT トークン**:JWT トークン ハンドラーは、ダウン ストリーム サービスで承認用に JWT トークンを作成するために使用できます。
