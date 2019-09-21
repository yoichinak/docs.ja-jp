---
title: Windows Identity Foundation 4.5 の概要
ms.date: 03/30/2017
ms.assetid: 5f723345-7270-49e2-b638-b3a34bd40517
author: BrucePerlerMS
ms.openlocfilehash: c9420ce641da32edc6196be0743d967446a14947
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045003"
---
# <a name="windows-identity-foundation-45-overview"></a>Windows Identity Foundation 4.5 の概要
Windows Identity Foundation 4.5 は、アプリケーション内でクレーム ベース ID を実装するための一連の .NET Framework クラスです。 このクラスを使用することで、クレーム対応アプリケーションおよびサービスのメリットを簡単に得られるようになります。 WIF 4.5 は、.NET Framework Version 4.5 以降が使用されているすべての Web アプリケーションまたは Web サービスで使用できます。 WIF は、オープン スタンダードに基づく業界共通の構想を取り入れた Microsoft のフェデレーション ID ソフトウェア ファミリの 1 つにすぎません。 フェデレーション Id は、次の3つのコンポーネントで構成します。[®フェデレーションサービスの Active Directory](https://go.microsoft.com/fwlink/?LinkID=247516)(AD FS) 2.0、 [Windows Azure Access Control Services](https://go.microsoft.com/fwlink/?LinkID=247517) (ACS)、WIF。 この 3 つのコンポーネントが一体となって、Microsoft の新しいクレーム ベースのクラウド ID およびアクセス プラットフォームのコアを形成しています。  
  
 WIF の詳細については、MSDN のセキュリティデベロッパーセンターの[Windows Identity Foundation の Web サイト](https://go.microsoft.com/fwlink/?LinkId=149009)を参照してください。 WIF を使用してアプリケーションを作成する方法の概要については、「 [Windows Identity Foundation](https://www.microsoftpressstore.com/store/programming-windows-identity-foundation-9780735627185)での Vittorio のプログラミング」を参照してください。  
  
## <a name="wif-45-features"></a>WIF 4.5 の機能  
 WIF 4.5 は、ID 対応アプリケーションをビルドするためのフレームワークです。 このフレームワークは、WS-Trust プロトコルと WS-Federation プロトコルを抽象化し、クレーム対応アプリケーションと、必要に応じてセキュリティ トークン サービス (STS) をビルドするための API を開発者に提供します。 アプリケーションでは、WIF を使用して、AD FS 2.0、ACS などの STS から発行されたトークンを処理し、Web アプリケーションまたは Web サービスで ID ベースの決定を下すことができます。  
  
 WIF 4.5 の主な機能は次のとおりです。  
  
- クレーム対応アプリケーション (証明書利用者アプリケーション) のビルド。 WIF は、開発者がクレーム対応アプリケーションをビルドするときに役立ちます。 WIF には、新しいクレーム モデルだけでなく豊富な API が用意されており、アプリケーション開発者は、この API を使用して、クレームに基づいてユーザー アクセスに関する決定を行うことができます。  また、アプリケーションを構築する環境として ASP.NET または WCF のどちらを選択した場合でも、WIF により一貫したプログラミングの操作性が実現します。  
  
- クレーム対応アプリケーションに対する ID 委任のサポートの構築。  WIF には、複数のサービスの境界を越えて元の要求元の ID を保持する機能が用意されています。 この機能を有効にするには、フレームワークで "ActAs" 機能または "OnBehalfOf" 機能のいずれかを使用します。開発者は、この機能を使用して、ID 委任のサポートをクレーム対応アプリケーションに追加できます。  
  
- カスタム STS のビルド。  WIF により、WS-Trust プロトコルをサポートするカスタム STS のビルドがかなり容易になりました。 この STS は、アクティブ STS とも呼ばれます。  
  
     また、フレームワークでは、WS-Federation をサポートする STS をビルドすることもでき、これにより Web ブラウザー クライアントが有効になります。 この STS は、パッシブ STS とも呼ばれます。  
  
- 新しい Identity and Access Tool for Visual Studio 11。このツールを使用すると、クレーム ベース ID を使用してアプリケーションを保護しながら、複数の ID プロバイダーからユーザーを受け入れることができます。 この WIF ツールは、次の URL からダウンロードでき<https://go.microsoft.com/fwlink/?LinkID=245849>ます。また、拡張機能マネージャーで "identity" を直接検索することで、Visual Studio 11 内から直接ダウンロードすることもできます。 詳細については、「[Visual Studio 2012 の ID およびアクセス ツール](identity-and-access-tool-for-vs.md)」を参照してください。  
  
 WIF がサポートする主なシナリオを次に示します。  
  
- フェデレーション。  WIF では、複数のパートナー間のフェデレーションを有効にできます。 開発者はクレーム対応アプリケーション (RP) およびカスタム STS をビルドするための機能を使用して、このシナリオを実現します。  
  
- ID の委任。  WIF ではサービスの境界を越えて ID を保持できるため、開発者は ID 委任のシナリオを簡単に実現できます。  
  
- ステップアップ認証。 同じアプリケーション内でも、リソースによって認証の要件が異なる場合があります。 WIF では、認証要件を段階的に厳しくする必要がある (たとえば、最初はユーザー名とパスワード認証でログインし、その後、スマート カード認証にステップアップする) アプリケーションを、開発者がビルドできます。  
  
 WIF を使用すると、クレーム ベースの ID モデルのメリットを簡単に利用できます。 詳細については、[開発者向けの Windows Identity Foundation のホワイト ペーパー](https://download.microsoft.com/download/7/d/0/7d0b5166-6a8a-418a-addd-95ee9b046994/windowsidentityfoundationwhitepaperfordevelopers-rtw.pdf)を参照してください。
