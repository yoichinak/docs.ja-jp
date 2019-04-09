---
title: WPF のセキュリティ方針 - セキュリティ エンジニアリング
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: c840912f755e1d6bf76720ad0178057c50e4cfd9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186161"
---
# <a name="wpf-security-strategy---security-engineering"></a>WPF のセキュリティ方針 - セキュリティ エンジニアリング
信頼できるコンピューティングは、セキュリティで保護されたコードの実稼働環境を確保するための Microsoft イニシアチブです。 信頼できるコンピューティング イニシアチブの重要な要素は、[!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)] です。 [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] は、セキュリティで保護されたコードの配信を容易にする標準のエンジニアリング プロセスと組み合わせて使用するエンジニアリングの方法です。 [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] は、ベスト プラクティスと形式化、測定可能性、追加の構造を組み合わせた 10 のフェーズで構成しています。それらは次のとおりです。  
  
-   セキュリティ設計の分析  
  
-   ツール ベースの品質チェック  
  
-   侵入テスト  
  
-   最終的なセキュリティ レビュー  
  
-   製品のリリース後のセキュリティ管理  
  
## <a name="wpf-specifics"></a>WPF 固有の仕様  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] エンジニアリング チームは、[!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] の適用と拡張の両方を行います。この組み合わせには、次の主要な側面があります。  
  
 [脅威モデリング](#threat_modeling)  
  
 [セキュリティ分析および編集ツール](#tools)  
  
 [テスト手法](#techniques)  
  
 [クリティカル コードの管理](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>脅威モデリング  
 脅威モデリングは、[!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] の主要コンポーネントで、システムをプロファイリングして潜在的なセキュリティの脆弱性を判断するために使用します。 脆弱性が特定されると、脅威モデリングは、常に適切な緩和策が存在することも保証します。  
  
 概略でとらえれば、食料品店を例にすると、脅威モデリングには次の主要な手順が含まれます。  
  
1.  **資産の特定**。 食料品店の資産には、従業員、安全、レジ、および在庫などがあります。  
  
2.  **エントリ ポイントの列挙**。 食料品店のエントリ ポイントには、玄関と裏口、窓、搬入口、および空調装置などがあります。  
  
3.  **エントリ ポイントを使用した資産に対する攻撃の調査**。 可能性のある攻撃の 1 つは、*空調設備*のエントリ ポイントを通じた食料品店の*安全*資産をターゲットとするものです。空調装置のねじが緩められると、そこから食糧品の安全が損なわれ、店自体の損失になる可能性があります。  
  
 脅威モデリングは [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 全体に適用されます。それは次のとおりです。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] パーサーのファイルの読み取り方法、対応するオブジェクト モデルのクラスへのテキストのマッピング方法、および実際のコードの作成方法。  
  
-   ウィンドウ ハンドル (hWnd) の作成方法、メッセージの送信方法、hWnd を使用したウィンドウの内容の表示方法。  
  
-   データ バインドがリソースを取得し、システムと対話する方法。  
  
 これらの脅威モデリングは、開発プロセス中のセキュリティ設計要件の識別と脅威の緩和策にとって重要です。  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>ソースの分析および編集ツール  
 [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] の手動セキュリティ コード レビュー要素に加えて、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] チームは、ソースの分析と関連する編集のためのいくつかのツールを使用してセキュリティの脆弱性を低減します。 さまざまなソースのツールを使用できます。それらは次のとおりです。  
  
-   **FXCop**:継承ルールからコード アクセス セキュリティと安全にアンマネージ コードと相互運用する方法の使用法に至るまで、マネージ コードでは、一般的なセキュリティ問題を検索します。 [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29) を参照してください。  
  
-   **Prefix/prefast**:バッファー オーバーラン、書式文字列の問題、エラー チェックなどのアンマネージ コードでは、セキュリティの脆弱性および一般的なセキュリティ問題を検索します。  
  
-   **Banned APIs**:ソースのセキュリティ問題の原因としてなどのよく知られている関数の偶発的な使用を識別するためにコードを検索`strcpy`します。 そのような関数が識別されると、よりセキュリティの高い代替手段に置き換えられます。  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>テスト手法  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] さまざまなセキュリティ テストを含む手法を使用します。  
  
-   **ホワイト ボックス テスト**:テスト担当者が、ソース コードを表示および悪用テストを作成し、  
  
-   **ブラック ボックス テスト**:テスト担当者は、API と機能を調査してセキュリティの悪用を検索しようし、製品を攻撃ましょう。  
  
-   **その他の製品から問題を再現セキュリティ**:該当する場合、関連する製品からのセキュリティの問題がテストされます。 たとえば、[!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] の約 60 のセキュリティの問題に適した変種を特定して、それが [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] に適用できるかどうかを試します。  
  
-   **ツール ベースの侵入テストを通じたファイルのファジー テスト**:ファイルのファジー化は、ファイル リーダーの悪用のさまざまな入力からの範囲を入力します。 この手法が使用される [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] の一例は、イメージ デコード コードでエラーを確認することです。  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>クリティカル コードの管理  
 [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)]、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]マークおよび特権を昇格させるセキュリティ クリティカルなコードを追跡するための .NET Framework のサポートを使用してセキュリティ サンド ボックスをビルド (を参照してください**セキュリティ クリティカルな手法**で[WPFセキュリティ方針 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md))。 セキュリティ クリティカルなコードに対して高度なセキュリティの品質要件を指定すると、このようなコードは、追加レベルのソース管理の制御とセキュリティの監査を受けします。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] の約 5 ～ 10% はセキュリティ クリティカルなコードで構成され、専用のレビュー チームによって確認されます。 ソース コードとチェックイン プロセスの管理は、セキュリティ クリティカルなコードを追跡し、各クリティカル エンティティ (重要なコードを含むメソッド) をサイン オフ状態にマップすることにより行われています。 サイン オフ状態には、1 つ以上のレビュー担当者の名前が含まれています。 毎日の [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] のビルドは、前のビルドのクリティカル コードと比較されて、承認されていない変更がチェックされます。 エンジニアがレビュー チームからの承認を得ずにクリティカル コードを変更すると、そのクリティカル コードはすぐに識別および修正されます。 このプロセスでは、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] サンドボックス コードで特に高いレベルの監視の適用と維持が可能になります。  
  
## <a name="see-also"></a>関連項目

- [セキュリティ](security-wpf.md)
- [WPF 部分信頼セキュリティ](wpf-partial-trust-security.md)
- [WPF のセキュリティ方針 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md)
- [信頼できるコンピューティング](https://www.microsoft.com/mscorp/twc/default.mspx)
- [.NET でのセキュリティ](../../standard/security/index.md)
