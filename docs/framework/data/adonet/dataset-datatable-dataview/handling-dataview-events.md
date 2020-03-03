---
title: DataView イベントの処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: c36c68b0375e7d03aac36de7d02b2c9579ea9316
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784588"
---
# <a name="handling-dataview-events"></a>DataView イベントの処理
<xref:System.Data.DataView.ListChanged> の <xref:System.Data.DataView> イベントを使用して、ビューが更新されているかどうかを確認できます。 基になるテーブルの行の追加、削除、または変更や、このスキーマの列の追加または削除、親子のリレーションシップの変更など、これらの更新を行うとこのイベントが発生します。 また、 **ListChanged**イベントは、表示している行の一覧が新しい並べ替え順序またはフィルターの適用によって大幅に変更された場合にも通知します。  
  
 **ListChanged**イベントは、 <xref:System.ComponentModel>名前空間の**listchangedeventhandler**デリゲートを実装し、オブジェクトを<xref:System.ComponentModel.ListChangedEventArgs>入力として受け取ります。 **ListChangedEventArgs**オブジェクトの**list type**プロパティの列挙値を<xref:System.ComponentModel.ListChangedType>使用して、発生した変更の種類を確認できます。 行の追加、削除、または移動を含む変更の場合、追加または移動された行の新しいインデックス、および削除された行の前のインデックスは、 **ListChangedEventArgs**オブジェクトの**NewIndex**プロパティを使用してアクセスできます。 移動された行の場合は、 **ListChangedEventArgs**オブジェクトの**oldindex**プロパティを使用して、移動された行の前のインデックスにアクセスできます。  
  
 また、 **DataViewManager**は、テーブルが追加または削除されたかどうか、または基になる**データセット**の**リレーション**コレクションに変更が加えられたかどうかを通知する**ListChanged**イベントも公開します。  
  
 次のコード例は、 **ListChanged**イベントハンドラーを追加する方法を示しています。  
  
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
