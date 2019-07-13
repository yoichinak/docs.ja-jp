---
title: '方法: Windows フォームのサイズ変更'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: aa7ee2bbbf6983a371ea71edc0dfd0cc12cd0c9d
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211664"
---
# <a name="how-to-resize-windows-forms"></a>方法: Windows フォームのサイズ変更

Windows フォームのサイズは、いくつかの方法で指定できます。 <xref:System.Windows.Forms.Form.Size%2A> プロパティに新しい値を設定したり、<xref:System.Windows.Forms.Control.Height%2A> プロパティまたは <xref:System.Windows.Forms.Control.Width%2A> プロパティを個別に調整したりすることで、フォームの高さと幅の両方をプログラムで変更できます。 Visual Studio を使用している場合は、Windows フォーム デザイナーを使用してサイズを変更できます。 参照してください[方法。デザイナーを使用して Windows フォームのサイズを変更](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))します。

## <a name="resize-a-form-programmatically"></a>フォームのサイズをプログラムで変更します。

フォームの <xref:System.Windows.Forms.Form.Size%2A> プロパティを設定して、実行時にフォームのサイズを定義します。

次のコード例では、フォームのサイズを 100 × 100 ピクセルに設定します。

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a>フォームの幅と高さをプログラムで変更します。

<xref:System.Windows.Forms.Form.Size%2A> を定義した後で、<xref:System.Windows.Forms.Control.Width%2A> プロパティまたは <xref:System.Windows.Forms.Control.Height%2A> プロパティを使用して、フォームの高さと幅のいずれかを変更します。

次のコード例は、フォームの幅を、フォームの左端から 300 ピクセルに設定し、高さは一定のままにする方法を示しています。

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

- または -

<xref:System.Windows.Forms.Form.Size%2A> プロパティを設定して、<xref:System.Drawing.Size.Width%2A> または <xref:System.Drawing.Size.Height%2A> を変更します。

ただし、次のコード例が示すように、この方法は、<xref:System.Windows.Forms.Control.Width%2A> プロパティまたは <xref:System.Windows.Forms.Control.Height%2A> プロパティをただ設定する方法よりも煩雑になります。

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a>フォームのサイズをプログラムで増分して変更します。

フォームのサイズを増分するには、<xref:System.Drawing.Size.Width%2A> プロパティと <xref:System.Drawing.Size.Height%2A> プロパティを設定します。

次のコード例は、フォームの幅を、現在の設定より 200 ピクセル広くする方法を示しています。

```vb
Form1.Width += 200
```

```csharp
Form1.Width += 200;
```

```cpp
Form1->Width += 200;
```

> [!CAUTION]
> <xref:System.Windows.Forms.Form.Size%2A> プロパティを新しい <xref:System.Drawing.Size> 構造に設定することにより高さと幅の両方のディメンションを同時に設定するというのでない限り、フォームのディメンションを変更するには、常に <xref:System.Drawing.Size.Height%2A> プロパティまたは <xref:System.Drawing.Size.Width%2A> プロパティを使用します。 <xref:System.Windows.Forms.Form.Size%2A> プロパティは、値型である <xref:System.Drawing.Size> 構造を返します。 値型のプロパティに新しい値を割り当てることはできません。 このため、次のコード例はコンパイルされません。

```vb
' NOTE: CODE WILL NOT COMPILE
Dim f As New Form()
f.Size.Width += 100
```

```csharp
// NOTE: CODE WILL NOT COMPILE
Form f = new Form();
f.Size.Width += 100;
```

```cpp
// NOTE: CODE WILL NOT COMPILE
Form^ f = gcnew Form();
f->Size->X += 100;
```

## <a name="see-also"></a>関連項目

- [Windows フォームについて](getting-started-with-windows-forms.md)
- [Windows フォーム アプリケーションの拡張](./advanced/index.md)
