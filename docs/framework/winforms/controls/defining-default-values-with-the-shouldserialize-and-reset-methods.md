---
title: ShouldSerialize メソッドと Reset メソッドによる既定値の定義
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: 609fe4896a2b01b8a69ff8a3d0854c85ddbd6a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969092"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>ShouldSerialize メソッドと Reset メソッドによる既定値の定義
`ShouldSerialize`と`Reset`は、プロパティに単純な既定値がない場合に、プロパティに対して指定できる省略可能なメソッドです。 プロパティに単純な既定値がある場合は、 <xref:System.ComponentModel.DefaultValueAttribute>を適用し、代わりに属性クラスコンストラクターに既定値を指定する必要があります。 これらのメカニズムのいずれかにより、デザイナーで次の機能が有効になります。

- プロパティは、既定値から変更されている場合、プロパティブラウザーで視覚的に表示されます。

- ユーザーはプロパティを右クリックし、 **[リセット]** をクリックして、プロパティを既定値に戻すことができます。

- デザイナーでは、より効率的なコードが生成されます。

    > [!NOTE]
    > を適用する<xref:System.ComponentModel.DefaultValueAttribute>か、 `Reset` *propertyname*メソッド`ShouldSerialize`と*propertyname*メソッドを指定します。 両方を使用しないでください。

 `Reset` *PropertyName*メソッドは、次のコードに示すように、プロパティを既定値に設定します。

```vb
Public Sub ResetMyFont()
   MyFont = Nothing
End Sub
```

```csharp
public void ResetMyFont() {
   MyFont = null;
}
```

> [!NOTE]
> プロパティに`Reset`メソッドがなく、が<xref:System.ComponentModel.DefaultValueAttribute>でマークされておらず、宣言`Reset`に既定値が指定されていない場合、そのプロパティのオプションは、の **[プロパティ]** ウィンドウのショートカットメニューで無効になります。Visual Studio の Windows フォームデザイナー。

 Visual Studio などのデザイナーでは`ShouldSerialize`、 *PropertyName*メソッドを使用して、プロパティが既定値から変更されたかどうかを確認し、プロパティが変更された場合にのみコードをフォームに記述します。これにより、コード生成をより効率的に行うことができます。 例えば:

```vb
'Returns true if the font has changed; otherwise, returns false.
' The designer writes code to the form only if true is returned.
Public Function ShouldSerializeMyFont() As Boolean
   Return Not (thefont Is Nothing)
End Function
```

```csharp
// Returns true if the font has changed; otherwise, returns false.
// The designer writes code to the form only if true is returned.
public bool ShouldSerializeMyFont() {
   return thefont != null;
}
```

 完全なコード例を次に示します。

```vb
Option Explicit
Option Strict

Imports System
Imports System.Windows.Forms
Imports System.Drawing

Public Class MyControl
   Inherits Control

   ' Declare an instance of the Font class
   ' and set its default value to Nothing.
   Private thefont As Font = Nothing

   ' The MyFont property.
   Public Property MyFont() As Font
      ' Note that the Font property never
      ' returns null.
      Get
         If Not (thefont Is Nothing) Then
            Return thefont
         End If
         If Not (Parent Is Nothing) Then
            Return Parent.Font
         End If
         Return Control.DefaultFont
      End Get
      Set
         thefont = value
      End Set
   End Property

   Public Function ShouldSerializeMyFont() As Boolean
      Return Not (thefont Is Nothing)
   End Function

   Public Sub ResetMyFont()
      MyFont = Nothing
   End Sub
End Class
```

```csharp
using System;
using System.Windows.Forms;
using System.Drawing;

public class MyControl : Control {
   // Declare an instance of the Font class
   // and set its default value to null.
   private Font thefont = null;

   // The MyFont property.
   public Font MyFont {
      // Note that the MyFont property never
      // returns null.
      get {
         if (thefont != null) return thefont;
         if (Parent != null) return Parent.Font;
         return Control.DefaultFont;
      }
      set {
         thefont = value;
      }
   }

   public bool ShouldSerializeMyFont() {
      return thefont != null;
   }

   public void ResetMyFont() {
      MyFont = null;
   }
}
```

 `MyFont`この場合、プロパティによってアクセスされるプライベート変数の値がであっ`null`ても、プロパティブラウザーには`null`表示されず、親<xref:System.Windows.Forms.Control.Font%2A> `null`のプロパティが表示されます。またはで<xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control>定義されている既定値。 したがって、の`MyFont`既定値を単に設定することはできません。また、を<xref:System.ComponentModel.DefaultValueAttribute>このプロパティに適用することはできません。 代わりに、 `MyFont`プロパティに`Reset`対してメソッドとメソッドを実装する必要があります。`ShouldSerialize`

## <a name="see-also"></a>関連項目

- [Windows フォーム コントロールのプロパティ](properties-in-windows-forms-controls.md)
- [プロパティの定義](defining-a-property-in-windows-forms-controls.md)
- [プロパティ変更イベント](property-changed-events.md)
