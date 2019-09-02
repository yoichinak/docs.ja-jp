---
title: DataSet のイベント処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 88f35d90f02b44b88f4bb7c6fac6a94a09afe81a
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204842"
---
# <a name="handling-dataset-events"></a>DataSet のイベント処理
<xref:System.Data.DataSet> オブジェクトには、 <xref:System.ComponentModel.MarshalByValueComponent.Disposed>、 <xref:System.Data.DataSet.Initialized>、 <xref:System.Data.DataSet.MergeFailed>という 3 つのイベントがあります。  
  
## <a name="the-mergefailed-event"></a>MergeFailed イベント  
 `DataSet` オブジェクトのイベントの中で最も使用頻度が高いイベントは、マージしようとしている `MergeFailed`オブジェクトのスキーマが競合する場合に発生する `DataSet` です。 この状況は、ターゲットとソースの <xref:System.Data.DataRow> が同じ主キー値を持ち、なおかつ、 <xref:System.Data.DataSet.EnforceConstraints%2A> プロパティが `true`に設定されている場合に発生します。 たとえば、マージ対象のテーブルの主キーの列が 2 つの `DataSet` オブジェクトのテーブル間で同じ場合、例外がスローされ、 `MergeFailed` イベントが発生します。 <xref:System.Data.MergeFailedEventArgs> イベントに渡される `MergeFailed` オブジェクトには、2 つの <xref:System.Data.MergeFailedEventArgs.Conflict%2A> オブジェクト間のスキーマで発生した競合を示す `DataSet` プロパティ、および競合が発生したテーブルの名前を示す <xref:System.Data.MergeFailedEventArgs.Table%2A> プロパティがあります。  
  
 次のコードは、`MergeFailed` イベントのイベント ハンドラーを追加する方法を示しています。  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a>Initialized イベント  
 <xref:System.Data.DataSet.Initialized> イベントは、 `DataSet` のコンストラクターによって `DataSet`の新しいインスタンスが初期化された後に発生します。  
  
 <xref:System.Data.DataSet.IsInitialized%2A> プロパティは、 `true` の初期化が完了した場合に `DataSet` を返します。それ以外の場合は `false`を返します。 この値は、 <xref:System.Data.DataSet.BeginInit%2A> の初期化を開始する `DataSet`メソッドによって <xref:System.Data.DataSet.IsInitialized%2A> が `false`に設定されます。 また、 <xref:System.Data.DataSet.EndInit%2A> の初期化を終了する `DataSet`メソッドによって `true`に設定されます。 これらのメソッドは、別のコンポーネントによって使用さ`DataSet`れているを初期化するために、Visual Studio のデザイン環境で使用されます。 通常、コード内で直接使用することはありません。  
  
## <a name="the-disposed-event"></a>Disposed イベント  
 `DataSet` は、 <xref:System.ComponentModel.MarshalByValueComponent> メソッドおよび <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> イベントの両方を公開する <xref:System.ComponentModel.MarshalByValueComponent.Disposed> クラスから派生しています。 イベント<xref:System.ComponentModel.MarshalByValueComponent.Disposed>は、コンポーネントの破棄されたイベントをリッスンするイベントハンドラーを追加します。 メソッドが呼び出され<xref:System.ComponentModel.MarshalByValueComponent.Disposed>たときに`DataSet`コードを実行する場合は、のイベントを使用できます。 <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>によって使用され<xref:System.ComponentModel.MarshalByValueComponent>ているリソースを解放します。  
  
> [!NOTE]
> オブジェクト`DataSet`および`DataTable`オブジェクトは、 <xref:System.ComponentModel.MarshalByValueComponent> から<xref:System.Runtime.Serialization.ISerializable>継承し、リモート処理用のインターフェイスをサポートします。 これらは、リモート処理ができる唯一の ADO.NET オブジェクトです。 詳細については、「 [.Net リモート処理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))」を参照してください。  
  
 を操作`DataSet`するときに使用できるその他のイベントの詳細については、「 [DataTable イベントの処理](handling-datatable-events.md)と[DataAdapter イベントの処理](../handling-dataadapter-events.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [DataSet、DataTable、および DataView](index.md)
- [データの検証](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))
- [ADO.NET でのデータの取得および変更](../retrieving-and-modifying-data.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
