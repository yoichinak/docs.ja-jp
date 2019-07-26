---
title: Default プロパティ アクセスは、インターフェイス '<defaultpropertyname>' の継承インターフェイス メンバー '<interfacename1>' とインターフェイス '<defaultpropertyname>' の '<interfacename2>' との間で不適切です。
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: a36cfe8e5496bbfd1941afa8a46086491ae96a2a
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512745"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>\<インターフェイス '\<interfacename1 > ' の継承インターフェイスメンバー ' defaultpropertyname > ' と interface '\<の '\<defaultpropertyname > ' の間で、既定のプロパティアクセスがあいまいですある可能性が > '

インターフェイスは、2つのインターフェイスから継承し、それぞれが同じ名前の既定のプロパティを宣言します。 コンパイラは、この既定のプロパティへのアクセスを修飾なしで解決することはできません。 次に例を示します。

```vb
Public Interface Iface1
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface2
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface3
    Inherits Iface1, Iface2
End Interface
Public Class testClass
    Public Sub accessDefaultProperty()
        Dim testObj As Iface3
        Dim testInt As Integer = testObj(1)
    End Sub
End Class
```

を指定`testObj(1)`すると、コンパイラはその値を既定のプロパティに解決しようとします。 ただし、継承されたインターフェイスにより、2つの既定のプロパティが考えられます。そのため、コンパイラはこのエラーを通知します。

**エラー ID:** BC30686

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 同じ名前のメンバーを継承しないようにしてください。 前の例では、 `testObj`がのメンバー ( `Iface2`たとえば、) を必要としない場合は、次のように宣言します。

  ```vb
  Dim testObj As Iface1
  ```

  \- または -

- 継承インターフェイスをクラスに実装します。 その後、継承された各プロパティを異なる名前で実装できます。 ただし、そのうちの1つだけが、実装するクラスの既定のプロパティになることができます。 次に例を示します。

  ```vb
  Public Class useIface3
      Implements Iface3
      Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop
          ' Insert code to define Get and Set procedures for prop1.
      End Property
      Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop
          ' Insert code to define Get and Set procedures for prop2.
      End Property
  End Class
  ```

## <a name="see-also"></a>関連項目

- [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
