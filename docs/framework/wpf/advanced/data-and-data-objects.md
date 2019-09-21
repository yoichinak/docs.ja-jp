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
ms.openlocfilehash: 4b948a64a14df7ea79b54b810f734056d57ef406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964861"
---
# <a name="data-and-data-objects"></a>データとデータ オブジェクト
ドラッグアンドドロップ操作の一部として転送されるデータは、データオブジェクトに格納されます。  概念的には、データオブジェクトは次のペアの1つ以上で構成されます。  
  
- 実際のデータを格納している。<xref:System.Object>  
  
- 対応するデータ形式識別子。  
  
 データ自体は、ベース<xref:System.Object>として表すことができるすべてのもので構成されます。  対応するデータ形式は文字列<xref:System.Type>で、データの形式に関するヒントを提供します。  データオブジェクトは、複数のデータ/データ形式のペアのホストをサポートします。これにより、1つのデータオブジェクトが複数の形式でデータを提供できるようになります。  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>データ オブジェクト  
 すべてのデータオブジェクトは、 <xref:System.Windows.IDataObject>インターフェイスを実装する必要があります。このインターフェイスは、データ転送を有効にし、容易にするために、次の標準的なメソッドセットを提供します。  
  
|メソッド|まとめ|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|指定したデータ形式でデータオブジェクトを取得します。|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|データが使用可能かどうか、または指定した形式に変換できるかどうかを確認します。|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|このデータオブジェクトのデータが格納されている形式の一覧、またはに変換できる形式の一覧を返します。|  
|<xref:System.Windows.IDataObject.SetData%2A>|指定されたデータをこのデータオブジェクトに格納します。|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クラスでのの<xref:System.Windows.IDataObject>基本的な実装を提供します。 <xref:System.Windows.DataObject> 多くの<xref:System.Windows.DataObject>一般的なデータ転送シナリオでは、stock クラスで十分です。  
  
 ビットマップ、CSV、ファイル、HTML、RTF、string、text、audio など、いくつかの定義済みの形式が定義されています。 に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]用意されている定義済みのデータ形式の詳細<xref:System.Windows.DataFormats>については、「クラスのリファレンス」を参照してください。  
  
 通常、データオブジェクトには、ある形式で格納されたデータをデータの抽出時に別の形式に自動的に変換する機能が含まれています。この機能は、自動変換と呼ばれます。 データオブジェクトで使用できるデータ形式に対してクエリを<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>実行する場合は、メソッドまたは<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>メソッドを呼び出し、 `autoConvert`パラメーターをと`false`して指定することによって、ネイティブデータ形式から自動変換可能なデータ形式をフィルター処理できます。  <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>メソッドを使用してデータオブジェクトにデータを追加する場合、 `autoConvert`パラメーターをに設定する`false`ことによって、データの自動変換を禁止できます。  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>データオブジェクトの操作  
 ここでは、データオブジェクトを作成および操作するための一般的な手法について説明します。  
  
### <a name="creating-new-data-objects"></a>新しいデータオブジェクトの作成  
 クラス<xref:System.Windows.DataObject>には、1つのデータ/データ形式<xref:System.Windows.DataObject>のペアで新しいインスタンスを簡単に設定できるようにする、オーバーロードされたコンストラクターがいくつか用意されています。  
  
 次のコード例では、新しいデータオブジェクトを作成し、オーバーロードさ<xref:System.Windows.DataObject.%23ctor%2A>れ<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>たコンストラクター () のいずれかを使用して、文字列と指定されたデータ形式でデータオブジェクトを初期化します。  この場合、データ形式は文字列で指定します。クラス<xref:System.Windows.DataFormats>には、定義済みの型文字列のセットが用意されています。 既定では、格納されたデータの自動変換は許可されています。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 データオブジェクトを作成するコードのその他の例については、「[データオブジェクトの作成](how-to-create-a-data-object.md)」を参照してください。  
  
### <a name="storing-data-in-multiple-formats"></a>複数の形式でのデータの格納  
 1つのデータオブジェクトは、複数の形式でデータを格納できます。   1つのデータオブジェクト内で複数のデータ形式を使用すると、データオブジェクトが、1つのデータ形式しか表現できない場合よりも広範なドロップターゲットによって消費される可能性があります。  通常、ドラッグ元は、潜在的なドロップターゲットで使用できるデータ形式については、依存関係がないことに注意してください。  
  
 次の例は、 <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>メソッドを使用して、複数の形式でデータオブジェクトにデータを追加する方法を示しています。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>使用可能な形式のデータオブジェクトのクエリ  
 1つのデータオブジェクトには任意の数のデータ形式を含めることができるため、データオブジェクトには使用可能なデータ形式の一覧を取得するための機能が含まれています。  
  
 次のコード例では<xref:System.Windows.DataObject.GetFormats%2A> 、オーバーロードを使用して、データオブジェクト (ネイティブと自動変換の両方) で使用できるすべてのデータ形式を示す文字列の配列を取得します。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 データオブジェクトに対して使用可能なデータ形式を照会するその他のコード例については、「[データオブジェクト内のデータ形式の一覧](how-to-list-the-data-formats-in-a-data-object.md)表示」を参照してください。  特定のデータ形式のデータオブジェクトに対してクエリを実行する例については、「データ[オブジェクトにデータ形式が存在するかどうかを判断](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)する」を参照してください。  
  
### <a name="retrieving-data-from-a-data-object"></a>データオブジェクトからのデータの取得  
 特定の形式のデータオブジェクトからデータを取得するには、 <xref:System.Windows.DataObject.GetData%2A>いずれかのメソッドを呼び出し、目的のデータ形式を指定するだけです。  <xref:System.Windows.DataObject.GetDataPresent%2A>メソッドの1つを使用して、特定のデータ形式が存在するかどうかを確認できます。  <xref:System.Windows.DataObject.GetData%2A>のデータ<xref:System.Object>を返します。データ形式によっては、このオブジェクトを型固有のコンテナーにキャストできます。  
  
 次のコード例では<xref:System.Windows.DataObject.GetDataPresent%28System.String%29> 、オーバーロードを使用して、指定されたデータ形式 (ネイティブまたは自動変換) が使用可能かどうかを確認します。 指定された形式が使用可能な場合、この例では<xref:System.Windows.DataObject.GetData%28System.String%29>メソッドを使用してデータを取得します。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 データオブジェクトからデータを取得するコードのその他の例については、「[特定のデータ形式でデータを取得](how-to-retrieve-data-in-a-particular-data-format.md)する」を参照してください。  
  
### <a name="removing-data-from-a-data-object"></a>データオブジェクトからのデータの削除  
 データオブジェクトからデータを直接削除することはできません。  データオブジェクトからデータを効果的に削除するには、次の手順を実行します。  
  
1. 保持するデータのみを含む新しいデータオブジェクトを作成します。  
  
2. 古いデータオブジェクトから新しいデータオブジェクトに必要なデータを "コピー" します。  データをコピーするには、いずれか<xref:System.Windows.DataObject.GetData%2A>のメソッドを使用<xref:System.Object>して、生データを含むを取得します。 <xref:System.Windows.DataObject.SetData%2A>次に、いずれかのメソッドを使用して、新しいデータオブジェクトにデータを追加します。  
  
3. 古いデータオブジェクトを新しいものに置き換えます。  
  
> [!NOTE]
> これら<xref:System.Windows.DataObject.SetData%2A>のメソッドは、データオブジェクトにデータを追加するだけです。データとデータ形式が前回の呼び出しとまったく同じであっても、データは置き換えられません。 同じ<xref:System.Windows.DataObject.SetData%2A>データとデータ形式に対してを2回呼び出すと、データオブジェクトにデータ/データ形式が2回存在することになります。
