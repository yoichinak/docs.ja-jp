---
title: DataView イベントの処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b625fad846c4c6cf008843bff1f6b0eabe0e1de4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151105"
---
# <a name="handling-dataview-events"></a>DataView イベントの処理
<xref:System.Data.DataView.ListChanged> の <xref:System.Data.DataView> イベントを使用して、ビューが更新されているかどうかを確認できます。 基になるテーブルの行の追加、削除、または変更や、このスキーマの列の追加または削除、親子のリレーションシップの変更など、これらの更新を行うとこのイベントが発生します。 **ListChanged**イベントは、新しい並べ替え順序またはフィルタの適用により、表示している行のリストが大幅に変更されたかどうかを通知します。  
  
 イベント**は**、名前空間の**ListChangedEventHandler**デリゲートを<xref:System.ComponentModel>実装し、オブジェクトの<xref:System.ComponentModel.ListChangedEventArgs>入力として受け取ります。 **オブジェクトの** **ListChangedType**プロパティの列挙値を<xref:System.ComponentModel.ListChangedType>使用して、どのような変更が発生したかを判断できます。 行の追加、削除、または移動を含む変更の場合、追加または移動された行の新しいインデックスと、削除された行の前のインデックスに **、ListChangedEventArgs**オブジェクトの**NewIndex**プロパティを使用してアクセスできます。 移動された行の場合は、**オブジェクト**の**OldIndex**プロパティを使用して、移動された行の前のインデックスにアクセスできます。  
  
 **また、テーブル**が追加または削除された場合、または基になる**DataSet**の**Relations**コレクションに変更が加えられた場合に通知する**ListChanged**イベントも公開されます。  
  
 次のコード例は **、ListChanged**イベント ハンドラーを追加する方法を示しています。  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [DataViews](dataviews.md)
- [ADO.NET の概要](../ado-net-overview.md)
