---
title: XamlWriter.Save のシリアル化の制限
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 96e917898320fb5d49f4e7dfc27daa7750af9d41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174369"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save のシリアル化の制限
API<xref:System.Windows.Markup.XamlWriter.Save%2A>を使用して、アプリケーションの内容を[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)][!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルとしてシリアル化できます。 ただし、正確にシリアル化される内容には、いくつかの顕著な制限があります。 これらの制限事項と一般的な考慮事項については、このトピックで説明します。  

<a name="Run_Time__Not_Design_Time_Representation"></a>
## <a name="run-time-not-design-time-representation"></a>デザイン時表現ではなく実行時  
 呼び出しによってシリアル化される基本的な哲学<xref:System.Windows.Markup.XamlWriter.Save%2A>は、結果が実行時にシリアル化されるオブジェクトの表現になるということです。 元[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のファイルのデザイン時プロパティの多くは、メモリ内オブジェクトとして読み込まれるまでに[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]既に最適化または失われている可能性があり、シリアル化を呼び出<xref:System.Windows.Markup.XamlWriter.Save%2A>したときには保持されません。 シリアル化された結果は、アプリケーションの構築された論理ツリーを効果的に表現したものですが、必ずしもアプリケーションを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]生成した元のツリーの表現ではありません。 これらの問題により、大規模な<xref:System.Windows.Markup.XamlWriter.Save%2A>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]デザイン サーフェイスの一部としてシリアル化を使用することは非常に困難になります。  
  
<a name="Serialization_is_Self_Contained"></a>
## <a name="serialization-is-self-contained"></a>シリアル化は自己完結型  
 のシリアル化された出力<xref:System.Windows.Markup.XamlWriter.Save%2A>は、自己完結型です。シリアル化されるすべてのものは、単一の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ルート要素を持つ単一のページ内に含まれ、URI 以外の外部参照はありません。 たとえば、ページがアプリケーション リソースからリソースを参照している場合、これらはシリアル化されるページのコンポーネントであるかのように表示されます。  
  
<a name="Extension_References_are_Dereferenced"></a>
## <a name="extension-references-are-dereferenced"></a>拡張参照が逆参照される  
 や`StaticResource``Binding`など、さまざまなマークアップ拡張機能の形式によって作成されるオブジェクトへの共通参照は、シリアル化プロセスによって逆参照されます。 これらは、メモリ内オブジェクトがアプリケーション ランタイムによって作成された時点で既に逆参照されており、<xref:System.Windows.Markup.XamlWriter.Save%2A>ロジックは、シリアル化された出力にこのような参照[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を復元するために元のオブジェクトを再検討しません。 これにより、データバインドまたはリソースが取得した値が、実行時表現で最後に使用された値となる可能性があり、その値をローカルで設定された他の値と区別する機能は制限付きまたは間接的に行われる可能性があります。 また、イメージは、元のソース参照としてではなく、プロジェクト内に存在するイメージに対するオブジェクト参照としてシリアル化され、元々参照されていたファイル名や URI は失われます。 同じページ内で宣言されたリソースも、リソース コレクションのキーとして保持されるのではなく、参照された場所にシリアル化されます。  
  
<a name="Event_Handling_is_Not_Preserved"></a>
## <a name="event-handling-is-not-preserved"></a>イベント処理が保持されない  
 を介して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]追加されたイベント ハンドラーがシリアル化されると、それらは保持されません。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]分離コードなし (および関連する x:Code メカニズムなし) ランタイム プロシージャ ロジックをシリアル化する方法はありません。 シリアル化は自己完結型であり、論理ツリーに限定されているため、イベント ハンドラを格納する機能はありません。 その結果、イベント ハンドラ属性 (属性自体と、ハンドラに名前を付けた文字列値) が出力[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]から削除されます。  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>XAMLWriter の使用に関する現実的なシナリオ。  
 ここに記載されている制限はかなり大きいですが、シリアル化に使用<xref:System.Windows.Markup.XamlWriter.Save%2A>する適切なシナリオはまだいくつかあります。  
  
- ベクター出力またはグラフィカル出力: 再ロード時に、レンダリングされた領域の出力を使用して、同じベクトルまたはグラフィックスを再現できます。  
  
- リッチ テキストドキュメントとフロー ドキュメント: テキストと、その中のすべての要素の書式設定と要素のコンテインメントは出力に保持されます。 これは、クリップボードの機能を近似するメカニズムに役立ちます。  
  
- ビジネス オブジェクト データの保持: XML データなどのカスタム要素にデータを格納している場合、ビジネス オブジェクトがカスタム[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コンストラクターの提供や参照渡しプロパティ値の変換などの基本的な規則に従っている限り、これらのビジネス オブジェクトはシリアル化によって永続化できます。
