---
title: XamlWriter.Save のシリアル化の制限
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 0416b92a6264e6a8261355197b4ab2fa61f80ef2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582593"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save のシリアル化の制限
API <xref:System.Windows.Markup.XamlWriter.Save%2A> は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの内容を [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルとしてシリアル化するために使用できます。 ただし、シリアル化される内容にはいくつかの注目すべき制限があります。 これらの制限といくつかの一般的な考慮事項については、このトピックで説明します。  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>実行時 (デザイン時の表現ではありません)  
 @No__t_0 の呼び出しによってシリアル化されるのは、実行時にシリアル化されるオブジェクトの表現になるという考え方です。 元の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルの多くのデザイン時プロパティは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] がメモリ内オブジェクトとして読み込まれる時間によって既に最適化されているか、または失われている可能性があり、シリアル化するために <xref:System.Windows.Markup.XamlWriter.Save%2A> を呼び出すと保持されません。 シリアル化された結果は、アプリケーションの構築された論理ツリーを効果的に表現したものですが、それを生成した元の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] であるとは限りません。 これらの問題により、広範な [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] デザインサーフェイスの一部として <xref:System.Windows.Markup.XamlWriter.Save%2A> シリアル化を使用することが非常に困難になります。  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>シリアル化は自己完結型です  
 @No__t_0 のシリアル化された出力は自己完結しています。シリアル化されるすべてのものは、1つのルート要素を持つ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の単一ページに含まれ、Uri 以外の外部参照は含まれません。 たとえば、ページがアプリケーションリソースからリソースを参照している場合、これらは、シリアル化されているページのコンポーネントであるかのように表示されます。  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>拡張機能の参照が逆参照されています  
 @No__t_0 や `Binding` など、さまざまなマークアップ拡張形式によって行われるオブジェクトへの一般的な参照は、シリアル化プロセスによって逆参照されます。 これらは、メモリ内のオブジェクトがアプリケーションランタイムによって作成された時点で既に逆参照されており、<xref:System.Windows.Markup.XamlWriter.Save%2A> ロジックは元の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を再参照して、シリアル化された出力への参照を復元しません。 これにより、データを取得した値が、実行時の表現によって最後に使用された値になる可能性があります。これにより、ローカルで他の値が設定された値を区別することができます。 また、イメージは、元のソース参照としてではなく、プロジェクトに存在するイメージへのオブジェクト参照としてシリアル化され、元に参照されたファイル名や URI が失われます。 同じページ内で宣言されたリソースも、リソースコレクションのキーとして保存されるのではなく、参照先のポイントにシリアル化されます。  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>イベント処理は保持されません  
 @No__t_0 によって追加されたイベントハンドラーは、シリアル化されても保持されません。 分離コードを使用せずに [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (また、関連する x:Code 機構も含まない)、ランタイム手続き型のロジックをシリアル化する方法がありません。 シリアル化は自己完結型であり、論理ツリーに限定されているため、イベントハンドラーを格納する機能はありません。 その結果、イベントハンドラー属性は、属性自体とハンドラーに名前を付けた文字列値の両方を出力 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] から削除されます。  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>XAMLWriter を使用するための現実的なシナリオ  
 ここに記載されている制限はかなり大きくなりますが、シリアル化に <xref:System.Windows.Markup.XamlWriter.Save%2A> を使用するための適切なシナリオもいくつかあります。  
  
- ベクターまたはグラフィカル出力: レンダリングされた領域の出力を使用して、再読み込み時に同じベクターまたはグラフィックスを再現できます。  
  
- リッチテキストおよびフロードキュメント: テキストおよびすべての要素の書式設定と要素の含有は、出力に保持されます。 これは、クリップボードの機能を推定するメカニズムに役立ちます。  
  
- ビジネスオブジェクトデータの保持: [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データなどのカスタム要素にデータを格納した場合、ビジネスオブジェクトが、参照渡しのプロパティ値のためのカスタムコンストラクターや変換の提供などの基本的な [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ルールに従う限り、オブジェクトは、シリアル化によってこれらできます。
