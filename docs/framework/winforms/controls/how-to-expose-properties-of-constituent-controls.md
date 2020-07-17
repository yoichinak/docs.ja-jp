---
title: '方法: 内在コントロールのプロパティを公開する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: f006e42771a5ecc71f6a508fd78d0e2dd8f2d2f2
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015874"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>方法: 内在コントロールのプロパティを公開する
複合コントロールを構成するコントロールは、*内在コントロール*と呼ばれます。 これらのコントロールは通常、プライベートとして宣言されるため、開発者がアクセスすることはできません。 これらのコントロールのプロパティを今後のユーザーが使用できるようにするには、それらをユーザーに公開する必要があります。 内在コントロールのプロパティは、ユーザーコントロールにプロパティを作成し、そのプロパティのアクセサー `get`と`set`アクセサーを使用して、内在コントロールのプライベートプロパティの変更を反映することによって公開されます。

 という名前`MyButton`の構成ボタンを持つ仮想的なユーザーコントロールを考えてみましょう。 この例では、ユーザーが`ConstituentButtonBackColor`プロパティを要求すると、の<xref:System.Windows.Forms.Control.BackColor%2A> `MyButton`プロパティに格納されている値が配信されます。 ユーザーがこのプロパティに値を割り当てた場合、 <xref:System.Windows.Forms.Control.BackColor%2A>その値はの`MyButton` `set`プロパティに自動的に渡され、コードが実行され、の`MyButton`色が変更されます。

 次の例は、構成ボタンの<xref:System.Windows.Forms.Control.BackColor%2A>プロパティを公開する方法を示しています。

```vb
Public Property ButtonColor() as System.Drawing.Color
   Get
      Return MyButton.BackColor
   End Get
   Set(Value as System.Drawing.Color)
      MyButton.BackColor = Value
   End Set
End Property
```

```csharp
public Color ButtonColor
{
   get
   {
      return(myButton.BackColor);
   }
   set
   {
      myButton.BackColor = value;
   }
}
```

### <a name="to-expose-a-property-of-a-constituent-control"></a>内在コントロールのプロパティを公開するには

1. ユーザーコントロールのパブリックプロパティを作成します。

2. プロパティの`get`セクションで、公開するプロパティの値を取得するコードを記述します。

3. プロパティの`set`セクションに、プロパティの値を、構成対象のコントロールの公開されたプロパティに渡すコードを記述します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.UserControl>
- [Windows フォーム コントロールのプロパティ](properties-in-windows-forms-controls.md)
- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
