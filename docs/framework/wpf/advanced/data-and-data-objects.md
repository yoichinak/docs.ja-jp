---
title: データとデータ オブジェクト
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
ms.openlocfilehash: 483491ea7408c1df57f31b4b984116b085ea50ba
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367545"
---
# <a name="data-and-data-objects"></a>データとデータ オブジェクト
ドラッグ アンド ドロップ操作の一部として転送されるデータは、データ オブジェクトに格納されます。  概念的には、データ オブジェクトは、次のペアの 1 つ以上で構成されます。  
  
-   <xref:System.Object>実際のデータを格納しています。  
  
-   対応するデータ形式の識別子。  
  
 データ自体をベースとして表すことができるもので構成できます<xref:System.Object>します。  対応するデータ形式は、文字列または<xref:System.Type>はデータの書式設定についてのヒントを提供します。  は複数のデータ/データ形式のペアをホストしているデータ オブジェクトのサポートこれにより、複数の形式でデータを提供する 1 つのデータ オブジェクト。  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>データ オブジェクト  
 すべてのデータ オブジェクトを実装する必要があります、<xref:System.Windows.IDataObject>を有効にして、データ転送を容易にするメソッドの次の標準セットを提供するインターフェイス。  
  
|メソッド|まとめ|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|指定したデータ形式のデータ オブジェクトを取得します。|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|データは、使用または指定した形式に変換できるかどうかを確認します。|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|このデータ オブジェクト内のデータでは、またはに変換できる形式の一覧を返します。|  
|<xref:System.Windows.IDataObject.SetData%2A>|このデータ オブジェクトには、指定したデータを格納します。|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 基本的な実装を提供します。<xref:System.Windows.IDataObject>で、<xref:System.Windows.DataObject>クラス。 ストック<xref:System.Windows.DataObject>クラスは、多くの一般的なデータ転送のシナリオだけで十分です。  
  
 ビットマップ、CSV、ファイル、HTML、RTF、文字列、テキスト、およびオーディオなど、いくつかの定義済みの形式があります。 提供される定義済みのデータ形式について[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を参照してください、<xref:System.Windows.DataFormats>クラスのリファレンス トピック。  
  
 通常、データ オブジェクトでは、データの抽出中に 1 つの形式を別の形式で格納されているデータを自動的に変換するための機能この機能は、自動変換と呼ばれます。 データ オブジェクトで使用可能なデータ形式のクエリを実行するときに自動変換できるデータ形式をフィルター処理するネイティブ データ形式から呼び出し、<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>または<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>メソッドを指定する、`autoConvert`パラメーターとして`false`します。  データを使用して、データ オブジェクトに追加するときに、<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>メソッド、データの自動変換は、設定によって禁止されることができます、`autoConvert`パラメーター`false`します。  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>データ オブジェクトの使用  
 このセクションでは、データ オブジェクトの作成と操作の一般的な手法について説明します。  
  
### <a name="creating-new-data-objects"></a>新しいデータ オブジェクトを作成します。  
 <xref:System.Windows.DataObject>クラスには、新しい設定を容易にするいくつかのオーバー ロードされたコンス トラクター<xref:System.Windows.DataObject>形式の 1 つのデータ/データ ペアでインスタンス。  
  
 次のコード例は、新しいデータ オブジェクトを作成し、オーバー ロードされたコンス トラクターのいずれかを使用して<xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) 文字列と指定したデータ形式でデータ オブジェクトを初期化します。  文字列でデータ形式を指定するこの例では、<xref:System.Windows.DataFormats>クラスは、一連の事前定義された型の文字列を提供します。 格納されたデータの自動変換は、既定で許可されます。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 データ オブジェクトを作成するコードの例については、[データ オブジェクトを作成](how-to-create-a-data-object.md)を参照してください。  
  
### <a name="storing-data-in-multiple-formats"></a>複数の形式でデータを格納します。  
 1 つのデータ オブジェクトは複数の形式でデータを格納できます。   1 つのデータ オブジェクト内で複数のデータ形式の戦略的な使用可能性があるとデータ オブジェクトはさまざまなよりもドロップ ターゲットで使用できるだけの場合、1 つのデータ形式を表すことができます。  なお、一般に、ドラッグ ソースが潜在的なドロップ ターゲットで使用できるデータ形式に依存しない必要があります。  
  
 次の例は、使用する方法を示します、<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>メソッドを複数の形式でデータ オブジェクトにデータを追加します。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>使用可能な形式のデータ オブジェクト クエリを実行します。  
 1 つのデータ オブジェクトは、任意の数のデータ形式を含めることができます、ために、データ オブジェクトには、使用可能なデータ形式の一覧を取得するための機能が含まれます。  
  
 次のコード例を使用して、 <xref:System.Windows.DataObject.GetFormats%2A> (ネイティブおよび自動変換によって) は、データ オブジェクトに使用可能なすべてのデータ形式を示す文字列の配列を取得するオーバー ロードします。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 使用可能なデータ形式のデータ オブジェクトのクエリを実行するコードの例については、[データ オブジェクト内のデータ形式を一覧表示](how-to-list-the-data-formats-in-a-data-object.md)を参照してください。  特定のデータ形式が存在するデータ オブジェクトのクエリを実行する例については、[データ形式が存在するかを判断、データ オブジェクトで](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)を参照してください。  
  
### <a name="retrieving-data-from-a-data-object"></a>データ オブジェクトからのデータの取得  
 いずれかを呼び出すことは、特定の形式でデータ オブジェクトからデータを取得するだけです、<xref:System.Windows.DataObject.GetData%2A>メソッドと目的のデータ形式を指定します。  1 つ、<xref:System.Windows.DataObject.GetDataPresent%2A>メソッドは、特定のデータ形式の有無を確認するために使用できます。  <xref:System.Windows.DataObject.GetData%2A> 内のデータを返します、 <xref:System.Object>; データの形式によってこのオブジェクトは、型固有のコンテナーにキャストすることができます。  
  
 次のコード例を使用して、<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>オーバー ロードを指定したデータ形式が使用可能なかどうかを確認する (ネイティブ コンパイルまたは自動変換によって)。 例を使用してデータを取得する指定の形式を使用できる場合、<xref:System.Windows.DataObject.GetData%28System.String%29>メソッド。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 データ オブジェクトからデータを取得するコードの例については、[特定のデータ形式でデータの取得](how-to-retrieve-data-in-a-particular-data-format.md)を参照してください。  
  
### <a name="removing-data-from-a-data-object"></a>データ オブジェクトからデータを削除します。  
 データ オブジェクトからデータを直接削除できません。  データ オブジェクトからデータを効果的に削除するには、次の手順を実行します。  
  
1.  保持するデータのみが格納される新しいデータ オブジェクトを作成します。  
  
2.  「コピー」old data オブジェクトから、新しいデータ オブジェクトへの必要なデータです。  データをコピーするには、いずれかを使用、<xref:System.Windows.DataObject.GetData%2A>を取得するメソッド、<xref:System.Object>生のデータが含まれていますのいずれかを使用する、<xref:System.Windows.DataObject.SetData%2A>新しいデータ オブジェクトにデータを追加するメソッド。  
  
3.  古いデータ オブジェクトを新しいものに置き換えます。  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A>メソッドは、データ オブジェクトにデータを追加するだけでは、データとデータ形式が正確に前回の呼び出しと同じ場合でも、データの置換は行いません。 呼び出す<xref:System.Windows.DataObject.SetData%2A>2 回の同じデータとデータ形式がデータ オブジェクトに 2 回存在しているデータ/データの形式で発生します。
