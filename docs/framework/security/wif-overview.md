---
title: Windows Identity Foundation 4.5 の概要
ms.date: 03/30/2017
ms.assetid: 5f723345-7270-49e2-b638-b3a34bd40517
author: BrucePerlerMS
ms.openlocfilehash: 6165dbf32b777a8d82e756f84ed2415d6ed3d774
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780095"
---
# <a name="windows-identity-foundation-45-overview"></a>Windows Identity Foundation 4.5 の概要
Windows Identity Foundation 4.5 は、アプリケーション内でクレーム ベース ID を実装するための一連の .NET Framework クラスです。 このクラスを使用することで、クレーム対応アプリケーションおよびサービスのメリットを簡単に得られるようになります。 WIF 4.5 は、.NET Framework Version 4.5 以降が使用されているすべての Web アプリケーションまたは Web サービスで使用できます。 WIF は、オープン スタンダードに基づく業界共通の構想を取り入れた Microsoft のフェデレーション ID ソフトウェア ファミリの 1 つにすぎません。 フェデレーション Id には、3 つのコンポーネントが構成されています。[Active Directory® フェデレーション サービス](https://go.microsoft.com/fwlink/?LinkID=247516)(AD FS) 2.0 では、 [Windows Azure の Access Control Services](https://go.microsoft.com/fwlink/?LinkID=247517) (ACS) は、WIF とします。 この 3 つのコンポーネントが一体となって、Microsoft の新しいクレーム ベースのクラウド ID およびアクセス プラットフォームのコアを形成しています。  
  
 WIF の詳細については、次を参照してください。、 [Windows Identity Foundation の Web サイト](https://go.microsoft.com/fwlink/?LinkId=149009)msdn Security Developer Center にします。 WIF を使用してアプリケーションの作成の概要については、次を参照してください。 [Windows Identity Foundation のプログラミング](https://go.microsoft.com/fwlink/?LinkId=210158)Vittorio bertocci が (Microsoft Press 発行)。  
  
## <a name="wif-45-features"></a>WIF 4.5 の機能  
 WIF 4.5 は、ID 対応アプリケーションをビルドするためのフレームワークです。 このフレームワークは、WS-Trust プロトコルと WS-Federation プロトコルを抽象化し、クレーム対応アプリケーションと、必要に応じてセキュリティ トークン サービス (STS) をビルドするための API を開発者に提供します。 アプリケーションでは、WIF を使用して、AD FS 2.0、ACS などの STS から発行されたトークンを処理し、Web アプリケーションまたは Web サービスで ID ベースの決定を下すことができます。  
  
 WIF 4.5 の主な機能は次のとおりです。  
  
- クレーム対応アプリケーション (証明書利用者アプリケーション) のビルド。 WIF は、開発者がクレーム対応アプリケーションをビルドするときに役立ちます。 WIF には、新しいクレーム モデルだけでなく豊富な API が用意されており、アプリケーション開発者は、この API を使用して、クレームに基づいてユーザー アクセスに関する決定を行うことができます。  また、アプリケーションを構築する環境として ASP.NET または WCF のどちらを選択した場合でも、WIF により一貫したプログラミングの操作性が実現します。  
  
- クレーム対応アプリケーションに対する ID 委任のサポートの構築。  WIF には、複数のサービスの境界を越えて元の要求元の ID を保持する機能が用意されています。 この機能を有効にするには、フレームワークで "ActAs" 機能または "OnBehalfOf" 機能のいずれかを使用します。開発者は、この機能を使用して、ID 委任のサポートをクレーム対応アプリケーションに追加できます。  
  
- カスタム STS のビルド。  WIF により、WS-Trust プロトコルをサポートするカスタム STS のビルドがかなり容易になりました。 この STS は、アクティブ STS とも呼ばれます。  
  
     また、フレームワークでは、WS-Federation をサポートする STS をビルドすることもでき、これにより Web ブラウザー クライアントが有効になります。 この STS は、パッシブ STS とも呼ばれます。  
  
- 新しい Identity and Access Tool for Visual Studio 11。このツールを使用すると、クレーム ベース ID を使用してアプリケーションを保護しながら、複数の ID プロバイダーからユーザーを受け入れることができます。 この WIF ツールは、次の URL からダウンロードできます:<https://go.microsoft.com/fwlink/?LinkID=245849>またはから直接、拡張機能マネージャーで直接"id"を検索して、Visual Studio 11。 詳細については、「[Visual Studio 2012 の ID およびアクセス ツール](../../../docs/framework/security/identity-and-access-tool-for-vs.md)」を参照してください。  
  
 WIF がサポートする主なシナリオを次に示します。  
  
- フェデレーション。  WIF では、複数のパートナー間のフェデレーションを有効にできます。 開発者はクレーム対応アプリケーション (RP) およびカスタム STS をビルドするための機能を使用して、このシナリオを実現します。  
  
- ID の委任。  WIF ではサービスの境界を越えて ID を保持できるため、開発者は ID 委任のシナリオを簡単に実現できます。  
  
- ステップアップ認証。 同じアプリケーション内でも、リソースによって認証の要件が異なる場合があります。 WIF では、認証要件を段階的に厳しくする必要がある (たとえば、最初はユーザー名とパスワード認証でログインし、その後、スマート カード認証にステップアップする) アプリケーションを、開発者がビルドできます。  
  
 WIF を使用すると、クレーム ベースの ID モデルのメリットを簡単に利用できます。 詳細については、[開発者向けの Windows Identity Foundation のホワイト ペーパー](https://download.microsoft.com/download/7/d/0/7d0b5166-6a8a-418a-addd-95ee9b046994/windowsidentityfoundationwhitepaperfordevelopers-rtw.pdf)を参照してください。
