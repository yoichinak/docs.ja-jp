---
title: クラウド ネイティブ アプリでの認証と承認
description: Azure 用クラウド ネイティブ .NET アプリの設計 |クラウド ネイティブ アプリでの認証と承認
ms.date: 03/02/2020
ms.openlocfilehash: 6261a0a72405bc1c984a04a7851aea4dd6664ddf
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805549"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>クラウドネイティブのアプリにおける認証と承認

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

*認証*は、セキュリティ プリンシパルの ID を決定するプロセスです。 *承認*とは、アクションを実行したり、リソースにアクセスしたりするための認証されたプリンシパルアクセス許可を付与する行為です。 認証がに短縮`AuthN`され、承認が に`AuthZ`短縮される場合があります。 クラウドネイティブ アプリケーションは、クライアントとアプリケーションの両方がどのプラットフォームまたはデバイス上で世界中のどこでも実行できるため、オープン HTTP ベースのプロトコルを使用してセキュリティ プリンシパルを認証する必要があります。 唯一の共通の要因は HTTP です。

多くの組織は、Active Directory フェデレーション サービス (ADFS) などのローカル認証サービスに依然として依存しています。 このアプローチは従来、オンプレミスの認証ニーズに適した組織に役立っていますが、クラウドネイティブアプリケーションは、クラウド専用に設計されたシステムから恩恵を受けています。 最近の2019年の英国国家サイバーセキュリティセンター(NCSC)のアドバイザリーは、「Azure AD を主要な認証ソースとして使用している組織は、実際には ADFS と比較してリスクを下げる」と述べています。 [この分析](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)で概説されている理由には、次のようなものがあります。

- Microsoft 資格情報保護テクノロジのフル セットへのアクセス。
- ほとんどの組織は、既にある程度 Azure AD に依存しています。
- NTLM ハッシュの二重ハッシュにより、ローカル Active Directory で動作する資格情報が侵害されないことが保証されます。

## <a name="references"></a>References

- [認証の基本](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [アクセス トークンとクレーム](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [オンプレミスの認証サービスを捨てる時が来たかもしれない](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[前へ](identity.md)
>[次へ](azure-active-directory.md)
