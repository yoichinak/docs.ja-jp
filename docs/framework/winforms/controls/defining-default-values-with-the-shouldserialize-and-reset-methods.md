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
ms.openlocfilehash: 5c95272c672d9b35d61e2fca8cccdbc532ef6776
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211298"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>ShouldSerialize メソッドと Reset メソッドによる既定値の定義
`ShouldSerialize` `Reset`プロパティで指定できる省略可能なメソッドをプロパティでない場合は、単純な既定値を設定します。 プロパティは、単純な既定値を持つ場合は適用して、<xref:System.ComponentModel.DefaultValueAttribute>代わりに、属性クラスのコンス トラクターを既定値を指定します。 これらのメカニズムのいずれかには、デザイナーで、次の機能が有効にします。

- プロパティが既定値から変更された場合、プロパティ ブラウザーでビジュアルを示す値を提供します。

- ユーザーは、プロパティを右クリックし、選択**リセット**プロパティを既定値に復元します。

- デザイナーより効率的なコードを生成します。

    > [!NOTE]
    >  いずれかが当てはまる、<xref:System.ComponentModel.DefaultValueAttribute>提供または`Reset` *PropertyName*と`ShouldSerialize` *PropertyName*メソッド。 どちらも使用しないでください。

 `Reset` *PropertyName*メソッドは、次のコード フラグメントで示すように、既定値にプロパティを設定します。

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
>  プロパティがない場合、`Reset`メソッドが設定されていない、<xref:System.ComponentModel.DefaultValueAttribute>に、その宣言で指定された既定値がないと、`Reset`オプションのショートカット メニューでそのプロパティが無効になっている、 **プロパティ** Visual Studio での Windows フォーム デザイナーのウィンドウ。

 Visual Studio などのデザイナーを使用して、 `ShouldSerialize` *PropertyName*プロパティが既定値から変更されたかどうかを確認し、プロパティを場合にのみフォームにコードを記述するメソッドが変更されたためより効率的なコードのことができます生成します。 例えば:

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

 完全なコード例に従います。

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

 この場合、プライベート変数の値にアクセスしている場合でも、`MyFont`プロパティは`null`、プロパティ ブラウザーが表示されない`null`代わりに、が表示されます、<xref:System.Windows.Forms.Control.Font%2A>でない場合は、親のプロパティ`null`、。既定値または<xref:System.Windows.Forms.Control.Font%2A>で定義されている値<xref:System.Windows.Forms.Control>します。 既定値ため`MyFont`、単に設定することはできません、<xref:System.ComponentModel.DefaultValueAttribute>このプロパティには適用できません。 代わりに、`ShouldSerialize`と`Reset`のメソッドを実装する必要があります、`MyFont`プロパティ。

## <a name="see-also"></a>関連項目

- [Windows フォーム コントロールのプロパティ](properties-in-windows-forms-controls.md)
- [プロパティの定義](defining-a-property-in-windows-forms-controls.md)
- [プロパティ変更イベント](property-changed-events.md)
