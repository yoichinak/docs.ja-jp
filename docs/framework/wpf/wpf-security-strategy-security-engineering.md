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
ms.openlocfilehash: a042f0ae1c7673f7d21b39580db3d373835939cd
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353833"
---
# <a name="wpf-security-strategy---security-engineering"></a>WPF のセキュリティ方針 - セキュリティ エンジニアリング
信頼できるコンピューティングは、セキュリティで保護されたコードの実稼働環境を確保するための Microsoft イニシアチブです。 信頼できるコンピューティングイニシアチブの重要な要素は、Microsoft セキュリティ開発ライフサイクル (Security Development Lifecycle: SDL) です。 SDL は、セキュリティで保護されたコードの配信を容易にするために、標準的なエンジニアリングプロセスと組み合わせて使用されるエンジニアリングプラクティスです。 SDL は10個のフェーズで構成されています。ここでは、ベストプラクティスとフォーム化、測定可能性、およびその他の構造を組み合わせることができます。  
  
- セキュリティ設計の分析  
  
- ツール ベースの品質チェック  
  
- 侵入テスト  
  
- 最終的なセキュリティ レビュー  
  
- 製品のリリース後のセキュリティ管理  
  
## <a name="wpf-specifics"></a>WPF 固有の仕様  
 @No__t 0 エンジニアリングチームは両方とも、次の主要な側面を含む、SDL の適用と拡張の両方を行います。  
  
 [脅威モデリング](#threat_modeling)  
  
 [セキュリティ分析および編集ツール](#tools)  
  
 [テスト手法](#techniques)  
  
 [クリティカル コードの管理](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>脅威モデリング  
 脅威のモデル化は、SDL の中核となるコンポーネントであり、潜在的なセキュリティの脆弱性を判断するためにシステムをプロファイリングするために使用されます。 脆弱性が特定されると、脅威モデリングは、常に適切な緩和策が存在することも保証します。  
  
 概略でとらえれば、食料品店を例にすると、脅威モデリングには次の主要な手順が含まれます。  
  
1. **資産の特定**。 食料品店の資産には、従業員、安全、レジ、および在庫などがあります。  
  
2. **エントリ ポイントの列挙**。 食料品店のエントリ ポイントには、玄関と裏口、窓、搬入口、および空調装置などがあります。  
  
3. **エントリ ポイントを使用した資産に対する攻撃の調査**。 可能性のある攻撃の 1 つは、*空調設備*のエントリ ポイントを通じた食料品店の*安全*資産をターゲットとするものです。空調装置のねじが緩められると、そこから食糧品の安全が損なわれ、店自体の損失になる可能性があります。  
  
 脅威モデリングは [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 全体に適用されます。それは次のとおりです。  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] パーサーのファイルの読み取り方法、対応するオブジェクト モデルのクラスへのテキストのマッピング方法、および実際のコードの作成方法。  
  
- ウィンドウ ハンドル (hWnd) の作成方法、メッセージの送信方法、hWnd を使用したウィンドウの内容の表示方法。  
  
- データ バインドがリソースを取得し、システムと対話する方法。  
  
 これらの脅威モデリングは、開発プロセス中のセキュリティ設計要件の識別と脅威の緩和策にとって重要です。  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>ソースの分析および編集ツール  
 SDL の手動のセキュリティコードレビュー要素に加えて、@no__t 0 のチームは、ソースの分析と関連する編集のために複数のツールを使用して、セキュリティの脆弱性を低減します。 さまざまなソースのツールを使用できます。それらは次のとおりです。  
  
- **FXCop**:継承規則からコードアクセスセキュリティの使用まで、アンマネージコードと安全に相互運用する方法に至るまで、マネージコードの一般的なセキュリティの問題を検出します。 [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29) を参照してください。  
  
- **Prefix/Prefast**:バッファーオーバーラン、書式設定文字列の問題、エラーチェックなど、アンマネージコードのセキュリティの脆弱性および一般的なセキュリティの問題を検出します。  
  
- **禁止 api**:ソースコードを検索して、セキュリティ上の問題 (`strcpy` など) の原因としてよく知られている関数を誤って使用していないかを特定します。 特定されると、これらの関数はより安全な代替手段に置き換えられます。  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>テスト手法  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] では、さまざまなテスト手法を使用します。それらは次のとおりです。  
  
- **ホワイトボックスのテスト**:テスト担当者はソースコードを表示し、exploit テストをビルドします。
  
- **ブラックボックステスト**:テスト担当者は、API と機能を調査してセキュリティの悪用を検出してから、製品の攻撃を試みます。  
  
- **他の製品からのセキュリティの問題を回帰**:関連する製品からのセキュリティ上の問題がテストされます。 たとえば、Internet Explorer について約60のセキュリティ問題の適切な亜種が特定され、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] に適用可能であることが確認されました。  
  
- **ファイルのファジー化を通じたツールベースの侵入テスト**:ファイルのファジー化は、さまざまな入力によってファイルリーダーの入力範囲を悪用することです。 この手法が使用される [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] の一例は、イメージ デコード コードでエラーを確認することです。  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>クリティカル コードの管理  
 @No__t 0 の場合、@no__t は、特権を昇格させるセキュリティクリティカルなコードをマークおよび追跡するための .NET Framework サポートを使用してセキュリティサンドボックスを構築します (「WPF のセキュリティ[方針-プラットフォームセキュリティ](wpf-security-strategy-platform-security.md)」の「**セキュリティクリティカルな方法**」を参照してください)。 セキュリティ クリティカルなコードに対して高度なセキュリティの品質要件を指定すると、このようなコードは、追加レベルのソース管理の制御とセキュリティの監査を受けします。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] の約 5 ～ 10% はセキュリティ クリティカルなコードで構成され、専用のレビュー チームによって確認されます。 ソース コードとチェックイン プロセスの管理は、セキュリティ クリティカルなコードを追跡し、各クリティカル エンティティ (重要なコードを含むメソッド) をサイン オフ状態にマップすることにより行われています。 サイン オフ状態には、1 つ以上のレビュー担当者の名前が含まれています。 毎日の [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] のビルドは、前のビルドのクリティカル コードと比較されて、承認されていない変更がチェックされます。 エンジニアがレビュー チームからの承認を得ずにクリティカル コードを変更すると、そのクリティカル コードはすぐに識別および修正されます。 このプロセスでは、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] サンドボックス コードで特に高いレベルの監視の適用と維持が可能になります。  
  
## <a name="see-also"></a>関連項目

- [Security](security-wpf.md)
- [WPF 部分信頼セキュリティ](wpf-partial-trust-security.md)
- [WPF のセキュリティ方針 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md)
- [信頼できるコンピューティング](https://www.microsoft.com/mscorp/twc/default.mspx)
- [.NET でのセキュリティ](../../standard/security/index.md)
