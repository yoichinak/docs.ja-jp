---
title: カスタム コントロールへのメソッドの実装
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], method implementation
- custom controls [Windows Forms], overloading methods
- custom controls [Windows Forms], method implementation
- methods [Windows Forms]
- methods [Windows Forms], custom controls
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
ms.openlocfilehash: 867bf97ea13654de6f9c0209c64b9320824f9665
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931750"
---
# <a name="method-implementation-in-custom-controls"></a>カスタム コントロールへのメソッドの実装
コントロールにメソッドを実装する方法は、他のコンポーネントにメソッドを実装する場合と同じです。  
  
 Visual Basic では、値を返す必要のあるメソッドは `Public Function` として実装されます。 値が返されない場合は、`Public Sub` として実装されます。 メソッドは次の構文で宣言します。  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 関数は値を返すため、整数、文字列、オブジェクトなど、戻り値の型を指定する必要があります。 `Function` プロシージャや `Sub` プロシージャが引数をとる場合は、引数も指定する必要があります。  
  
 Visual Basic とは異なり、C# では関数とプロシージャが区別されません。 メソッドは値を返すか、または `void` を返します。 C# のパブリック メソッドを宣言する構文は次のとおりです。  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 メソッドを宣言する際、可能な限り、メソッドのすべての引数を明示的なデータ型として宣言します。 オブジェクト参照を使用する引数は、特定のクラス型として宣言される必要があります (例: `As Widget` ではなく、`As Object`)。 Visual Basic では、既定の設定 `Option Strict` によって自動的にこの規則が適用されます。  
  
 型付き引数を使用することにより、開発者によるエラーの多くを、実行時ではなく、コンパイラによって検出できます。 コンパイラは常に多くのエラーを検出するのに対し、ランタイム テストは、テスト スイートと同程度の精度しかありません。  
  
## <a name="overloaded-methods"></a>オーバーロードされたメソッド  
 コントロールのユーザーが、メソッドにさまざまなパラメーターの組み合わせを指定できるようにするには、明示的なデータ型を使用して、メソッドのオーバーロードを複数提供します。 テスト時にエラーが検出されない場合があるため、任意のデータ型を含めることのできる `As Object` として宣言するパラメーターは作成しないでください。  
  
> [!NOTE]
> 共通言語ランタイムの汎用データ型は、`Object` ではなく、`Variant` です。 `Variant` は、言語から削除されました。  
  
 たとえば、`Spin` という仮想のコントロールに `Widget` メソッドがあり、スピンの方向と速度を直接指定するか、角運動量を吸収する他の `Widget` オブジェクトを指定できます。  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a>関連項目

- [イベント](../../../standard/events/index.md)
- [Windows フォーム コントロールのプロパティ](properties-in-windows-forms-controls.md)
