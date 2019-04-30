---
title: XAML セキュリティの考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 124310497cc2a8e8a816ba90b2c68a16ed342ae6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938789"
---
# <a name="xaml-security-considerations"></a>XAML セキュリティの考慮事項
このトピックでは、XAML と .NET Framework XAML サービス API を使用すると、アプリケーションのセキュリティのベスト プラクティスをについて説明します。  
  
## <a name="untrusted-xaml-in-applications"></a>アプリケーションで信頼されていない XAML  
 最も一般的な意味で、信頼されていない XAML は、アプリケーションのインクルードまたは出力しなかった具体的にはない任意の XAML ソースです。  
  
 XAML にコンパイルまたはとして格納されている、 `resx`-信頼された署名済みアセンブリ内の型のリソースが本質的に信頼されていません。 アセンブリ全体を信頼するよう、XAML を信頼することができます。 ほとんどの場合、信頼の側面をストリームまたはその他の I/O から読み込む XAML ソースでは、loose XAML 懸念しているだけです。 Loose XAML は、特定のコンポーネントまたは展開パッケージのインフラストラクチャとアプリケーション モデルの機能ではありません。 ただし、アセンブリは、loose XAML を読み込む必要がある動作を実装する場合があります。  
  
 信頼されていない XAML を扱う必要があります、一般に、同じ信頼できないコードの場合と同様。 XAML の信頼されていない可能性がありますが、信頼されるコードにアクセスすることを防ぐために、サンド ボックスまたは他のメタファを使用します。  
  
 XAML の機能の性質には、XAML オブジェクトを構築し、プロパティを設定する権限が付与されます。 これらの機能も含まれます型コンバーター、マッピング、およびマークアップ拡張機能を使用して、アプリケーション ドメインにアセンブリへのアクセスにアクセスする`x:Code`ブロック、という具合です。  
  
 その言語レベルの機能に加え、XAML は、多くのテクノロジの UI の定義に使用されます。 信頼されていない XAML を読み込むには、悪意のなりすまし UI を読み込む可能性があります。  
  
## <a name="sharing-context-between-readers-and-writers"></a>リーダーとライターの間でコンテキストを共有  
 XAML リーダーと XAML ライターの .NET Framework XAML サービス アーキテクチャでは、多くの場合、XAML リーダーが XAML ライターでは、または共有 XAML スキーマ コンテキストを共有が必要です。 オブジェクトまたはコンテキストを共有する必要があります、XAML ノード ループのロジックを記述するか、パスを保存するカスタムを提供する場合。 XAML リーダー インスタンス、既定以外の XAML スキーマ コンテキスト、または信頼されていると信頼されていないコード間での XAML リーダー/ライター クラスの設定を共有しないでください。  
  
 ほとんどのシナリオと XAML オブジェクトのバッキング CLR ベースの型の記述に関連する操作では、既定の XAML スキーマ コンテキストだけを使用できます。 既定の XAML スキーマ コンテキストは、完全な信頼を損なうおそれのある設定を明示的に含まれません。 信頼と信頼されていない XAML リーダー/ライター コンポーネント間のコンテキストを共有する安全ななります。 ただし、これを行うと、それがこのようなリーダーとライターを個別に保持することをお勧め<xref:System.AppDomain>具体的には意図した/セキュリティで保護された部分信頼のうちの 1 つのスコープ。  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>XAML 名前空間とアセンブリの信頼レベル  
 非修飾の基本的な構文と XAML がアセンブリにカスタム XAML 名前空間のマッピングを解釈する方法の定義は、アプリケーション ドメインに読み込まれた、信頼できる、信頼されていないアセンブリは区別されません。 したがって、信頼されたアセンブリの目的の XAML 名前空間マッピングを偽装し、XAML ソースの宣言されたオブジェクトおよびプロパティ情報をキャプチャする信頼されていないアセンブリを技術的に可能は。 このような状況を回避するためにセキュリティ要件があれば、次の手法の 1 つを使用して、目的の XAML 名前空間のマッピングを行う必要があります。  
  
- アプリケーションの XAML によって行われたすべての XAML 名前空間マッピングで厳密な名前でアセンブリの完全修飾名を使用します。  
  
- アセンブリの特定を構築することで、参照アセンブリの固定セットへのマッピングを制限する<xref:System.Xaml.XamlSchemaContext>XAML リーダーと XAML オブジェクト ライター。 以下を参照してください。<xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>XAML の型マッピングとシステム アクセスの種類  
 XAML では、さまざまな方法では CLR が基本的な CLR 型システムを実装する方法のピアが独自の型システムをサポートします。 ただし、その型の情報に基づいた型に関する信頼の決定を行っている型の対応の特定の要素の型のバッキング CLR の型情報に従う必要があります。 これは、仮想メソッドとして開いたまま、XAML 型システムの特定のレポート機能の一部はそのため、完全に元の .NET Framework XAML サービス実装の管理下にあるためです。 XAML 型システムでは、XAML 自体の拡張機能と、既定の実装で CLR を基盤と既定の XAML スキーマ コンテキストと代替可能な型マッピング戦略に合わせて拡張可能なために、これらの拡張ポイントが存在します。 詳細については、のプロパティのいくつかの固有の注意事項を参照してください。<xref:System.Xaml.XamlType>と<xref:System.Xaml.XamlMember>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xaml.Permissions.XamlAccessLevel>
