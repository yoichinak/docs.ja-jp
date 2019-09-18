---
title: Identity and Access Tool for Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: d58cca13dc3ac67742e5371aed628a6a680e61e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045424"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a>Identity and Access Tool for Visual Studio 2012
このトピックでは、新しい Identity and Access Tool for Visual Studio 11 について説明します。 このツールは、次の URL からダウンロードでき<https://go.microsoft.com/fwlink/?LinkID=245849>ます。または、拡張機能マネージャーで "identity" を直接検索することで、Visual Studio 11 内から直接ダウンロードできます。  
  
 Identity and Access Tool for Visual Studio 11 の特長を次に示します。これにより、開発時の操作性が大幅に簡素化されます。  
  
- 新しいツールを使用すると、Web アプリケーション プロジェクトの種類およびターゲット IIS Express を使用して開発できます。  
  
- ブランケット保護のみの認証とは異なり、新しいツールによって、ローカルのホーム レルム探索ページ/コントローラー (または、アプリケーション内で認証によって実行されるその他のエンドポイント処理) を指定できます。WIF は要求の構成を変更して、認証されていないすべての要求が、STS ではなくその場所にリダイレクトされるようにします。  
  
- ツールには、テスト セキュリティ トークン サービス (STS) が含まれています。この STS は、デバッグ セッションの起動時にローカル コンピューターで実行されます。 したがって、アプリケーションのテストに必要なクレームを取得する目的で、カスタム STS プロジェクトを作成して調整する必要はありません。 クレームの種類と値は完全にカスタマイズできます。  
  
- ツールの UI を使用して共通の設定を直接変更できます。web.config を編集する必要はありません。  
  
- Active Directory フェデレーション サービス (AD FS) 2.0 (または、他の WS-Federation プロバイダー) を使用して、1 つの画面でフェデレーションを確立できます。  
  
- このツールでは、Windows Azure Access Control Service (ACS) の機能を使用するすべての id プロバイダーのチェックボックスの一覧が表示されます。Facebook、Google、Live ID、Yahoo!、OpenID プロバイダー、および任意の WS-FEDERATION プロバイダー。 ID プロバイダーのチェック ボックスをオンにして、[OK] をクリックし、F5 キーを押すと、アプリケーションと ACS の両方が自動的に構成され、テスト アプリケーションが ACS 対応になります。  
  
## <a name="see-also"></a>関連項目

- [WIF の機能](wif-features.md)
