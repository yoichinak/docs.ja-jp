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
ms.openlocfilehash: 532c254f997da183b073ddc9e00b4364ecfcd739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186346"
---
# <a name="data-and-data-objects"></a>データとデータ オブジェクト
ドラッグ アンド ドロップ操作の一部として転送されるデータは、データ オブジェクトに格納されます。  概念的には、データ オブジェクトは、次の 1 つ以上のペアで構成されます。  
  
- 実際<xref:System.Object>のデータを含む。  
  
- 対応するデータ形式識別子。  
  
 データ自体は、 ベース<xref:System.Object>として表現できる何でもで構成できます。  対応するデータ形式は文字列であるか<xref:System.Type>、データの形式に関するヒントを提供します。  データ オブジェクトは、複数のデータ/データ形式のペアのホストをサポートします。これにより、単一のデータ オブジェクトが複数の形式でデータを提供できます。  
  
<a name="Data_and_Data_Objects"></a>
## <a name="data-objects"></a>データ オブジェクト  
 すべてのデータ オブジェクトは、<xref:System.Windows.IDataObject>データ転送を有効にし、容易にする次の標準的なメソッドセットを提供するインターフェイスを実装する必要があります。  
  
|Method|まとめ|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|データ オブジェクトを指定したデータ形式で取得します。|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|データが指定した形式で使用可能かどうか、または指定した形式に変換可能かどうかをチェックします。|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|このデータ オブジェクトのデータが格納されているか、または変換可能である形式のリストを返します。|  
|<xref:System.Windows.IDataObject.SetData%2A>|指定したデータをこのデータ オブジェクトに格納します。|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、クラス<xref:System.Windows.IDataObject>の基本的な実装<xref:System.Windows.DataObject>を提供します。 在庫<xref:System.Windows.DataObject>クラスは、多くの一般的なデータ転送シナリオで十分です。  
  
 ビットマップ、CSV、ファイル、HTML、RTF、文字列、テキスト、オーディオなど、定義済みのフォーマットがいくつかあります。 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供される定義済みのデータ形式については、クラスのリファレンストピック<xref:System.Windows.DataFormats>を参照してください。  
  
 データ オブジェクトには、通常、データを抽出するときに、ある形式で格納されたデータを別の形式に自動的に変換する機能が含まれます。この機能は自動変換と呼ばれます。 データ オブジェクトで使用できるデータ形式を照会する場合、 <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> or<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>メソッドを呼び出してパラメーターを`autoConvert``false`に指定することで、自動変換可能なデータ形式をネイティブ データ形式からフィルター処理できます。  メソッドを使用してデータオブジェクトにデータを<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>追加する場合、パラメータを`autoConvert``false`に設定することでデータの自動変換を禁止できます。  
  
<a name="Working_with_Data_Objects"></a>
## <a name="working-with-data-objects"></a>データ オブジェクトの操作  
 このセクションでは、データ オブジェクトを作成および操作するための一般的な手法について説明します。  
  
### <a name="creating-new-data-objects"></a>新しいデータ オブジェクトの作成  
 この<xref:System.Windows.DataObject>クラスには、単一のデータ/データ形式のペアで新しい<xref:System.Windows.DataObject>インスタンスを簡単に設定するための、オーバーロードされた複数のコンストラクターが用意されています。  
  
 次のコード例では、新しいデータ オブジェクトを作成し、オーバーロードされたコンストラクター <xref:System.Windows.DataObject.%23ctor%2A><xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>( ) のいずれかを使用して、文字列と指定したデータ形式でデータ オブジェクトを初期化します。  この場合、データ形式は文字列で指定されます。この<xref:System.Windows.DataFormats>クラスは、定義済みの型文字列のセットを提供します。 デフォルトでは、格納されたデータの自動変換が可能です。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 データ オブジェクトを作成するコードの例については、「[データ オブジェクトの作成](how-to-create-a-data-object.md)」を参照してください。  
  
### <a name="storing-data-in-multiple-formats"></a>複数の形式でのデータの格納  
 1 つのデータ オブジェクトは、複数の形式でデータを格納できます。   単一のデータ オブジェクト内で複数のデータ形式を戦略的に使用すると、単一のデータ形式しか表現できない場合よりも、データ オブジェクトが幅広いドロップ ターゲットによって消費される可能性があります。  一般に、ドラッグ ソースは、潜在的なドロップ ターゲットによって消費されるデータ形式に関しては、まったく問題がない必要があります。  
  
 メソッドを使用して、複数の<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>形式のデータ オブジェクトにデータを追加する方法を次の例に示します。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>データ オブジェクトに使用可能な形式を照会する  
 1 つのデータ オブジェクトには任意の数のデータ形式を含めることができるため、データ オブジェクトには、使用可能なデータ形式のリストを取得するための機能が含まれます。  
  
 次のコード例では、<xref:System.Windows.DataObject.GetFormats%2A>オーバーロードを使用して、データ オブジェクトで使用できるすべてのデータ形式 (ネイティブと自動変換の両方) を示す文字列の配列を取得します。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 データ オブジェクトに使用可能なデータ形式を照会するコードの例については、「[データ オブジェクトにデータ形式をリストする](how-to-list-the-data-formats-in-a-data-object.md)」を参照してください。  データ オブジェクトに対して特定のデータ形式が存在するかどうかのクエリの例については、「[データ 形式がデータ オブジェクトに存在するかどうかを判断](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)する 」を参照してください。  
  
### <a name="retrieving-data-from-a-data-object"></a>データ オブジェクトからのデータの取得  
 特定の形式でデータ オブジェクトからデータを取得するには、<xref:System.Windows.DataObject.GetData%2A>メソッドの 1 つを呼び出して目的のデータ形式を指定するだけです。  メソッドの<xref:System.Windows.DataObject.GetDataPresent%2A>1 つを使用して、特定のデータ形式の有無をチェックできます。  <xref:System.Windows.DataObject.GetData%2A>でデータを返します<xref:System.Object>。データ形式に応じて、このオブジェクトを型固有のコンテナーにキャストできます。  
  
 次のコード例では、<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>指定したデータ形式 (ネイティブまたは自動変換) が使用可能かどうかを調べるオーバーロードを使用します。 指定した形式が使用可能な場合、この例では、メソッドを使用して<xref:System.Windows.DataObject.GetData%28System.String%29>データを取得します。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 データ オブジェクトからデータを取得するコードの例については、「特定の[データ形式でデータを取得する](how-to-retrieve-data-in-a-particular-data-format.md)」を参照してください。  
  
### <a name="removing-data-from-a-data-object"></a>データ オブジェクトからのデータの削除  
 データ オブジェクトからデータを直接削除することはできません。  データ オブジェクトからデータを効果的に削除するには、次の手順を実行します。  
  
1. 保持するデータのみを含む新しいデータ オブジェクトを作成します。  
  
2. 古いデータ オブジェクトから新しいデータ オブジェクトに目的のデータをコピーします。  データをコピーするには、いずれかのメソッドを<xref:System.Windows.DataObject.GetData%2A>使用して生データを<xref:System.Object>含む を取得し、その<xref:System.Windows.DataObject.SetData%2A>メソッドの 1 つを使用して新しいデータ オブジェクトにデータを追加します。  
  
3. 古いデータ オブジェクトを新しいデータ オブジェクトに置き換えます。  
  
> [!NOTE]
> メソッド<xref:System.Windows.DataObject.SetData%2A>はデータオブジェクトにのみデータを追加します。データとデータ形式が前回の呼び出しとまったく同じであっても、データは置き換わりません。 同<xref:System.Windows.DataObject.SetData%2A>じデータとデータ形式に対して 2 回呼び出すと、データ/データ形式がデータ オブジェクト内に 2 回存在します。
