---
title: XamlWriter.Save のシリアル化の制限
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: f743f3de505904854be8aab59e9d3ad14ee64581
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238619"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save のシリアル化の制限
API<xref:System.Windows.Markup.XamlWriter.Save%2A>の内容をシリアル化に使用できる、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]としてアプリケーションを[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイル。 ただし、シリアル化されるいくつかの注目すべき制限があります。 このトピックでは、これらの制限事項といくつかの一般的な考慮事項が記載されています。  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>実行時、デザイン時のない表現  
 呼び出しによって何がシリアル化の基本的な考え方<xref:System.Windows.Markup.XamlWriter.Save%2A>結果が実行時に、シリアル化されるオブジェクトの表現になることができます。 元の多くのデザイン時プロパティ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルが既に最適化されたかまたは時間によって失われる可能性を[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]がメモリ内のオブジェクトとして読み込まれを呼び出す場合は保持されません<xref:System.Windows.Markup.XamlWriter.Save%2A>をシリアル化します。 シリアル化された結果は、アプリケーションの必ずしも元は、構築済みの論理ツリーの有効な表現[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]結果を生成します。 これらの問題を行う非常に難しく、<xref:System.Windows.Markup.XamlWriter.Save%2A>拡張の一部としてシリアル化[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]デザイン サーフェイス。  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>シリアル化は、自己完結型  
 シリアル化された出力<xref:System.Windows.Markup.XamlWriter.Save%2A>は自己完結型; 内に含まれるすべてのシリアル化することは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]単一ページで、単一のルート要素、および以外の外部参照はありません[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]します。 たとえば場合は、ページには、アプリケーション リソースからのリソースが参照されている、シリアル化されるページのコンポーネントがあった場合のように表示されます。  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>拡張機能の参照が逆参照します。  
 一般的なオブジェクトへの参照などのマークアップ拡張機能のさまざまな形式で行われた`StaticResource`または`Binding`、シリアル化プロセスの逆参照します。 既にこれらがメモリ内オブジェクトには、アプリケーションの実行によって作成された時に逆参照される、<xref:System.Windows.Markup.XamlWriter.Save%2A>ロジックは、元を再検討していない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]シリアル化された出力には、このような参照を復元します。 これは可能性のある、任意のデータ バインドまたは最後に、実行時で表現したローカル設定の他の値からこのような値を区別するためにのみ制限付きまたは間接の機能を使用する値を指定する値を取得したリソースがフリーズします。 任意のファイル名が失われる元のソースの参照としてではなく、プロジェクト内に存在するために、イメージはイメージへの参照をオブジェクトとしてシリアル化もまたは[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]最初に参照します。 同じページ内で宣言されているリソースは、それらが参照されている場所、リソース コレクションのキーとして保持されるのではなく、ポイントにシリアル化されたで認識されています。  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>イベント処理が保持されません。  
 場合によって追加されたイベント ハンドラー[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]はシリアル化すると、それらは保持されません。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 分離コードなし (ともに関連する x: コードのメカニズムがなければ)、手続き型のロジックをランタイム シリアル化することはできません。 シリアル化が自己完結型の論理ツリーに限定的であるために、イベント ハンドラーを格納するための機能はありません。 出力からイベント ハンドラーの属性、属性自体と、ハンドラーの名前を示す文字列値の両方を削除するため、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>(XAMLWriter.Save の) 使用するための現実的なシナリオ  
 制限事項が表示されているときにここでは相当を使用するためのいくつかの適切なシナリオはまだあります<xref:System.Windows.Markup.XamlWriter.Save%2A>のシリアル化します。  
  
- ベクトルまたはグラフィカルな出力:レンダリングされた領域の出力は、同じベクターまたは再読み込み時のグラフィックスを再現するために使用できます。  
  
- リッチ テキストおよびフロー ドキュメント:テキストとすべての要素の書式設定と要素コンテインメント内には、出力に保持されます。 おおよそのクリップボード機能のメカニズムの便利なことができます。  
  
- ビジネス オブジェクト データの保持。保存しているかどうかのデータをカスタムの要素になど[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データ、ビジネス オブジェクトは、次の基本的なかぎり[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]など、カスタム コンス トラクターと参照渡しでプロパティ値の変換を提供するルールは、これらのビジネス オブジェクトを指定できますシリアル化を通じて永続的なものです。
