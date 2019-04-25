---
title: Default プロパティ アクセスは、インターフェイス '<defaultpropertyname>' の継承インターフェイス メンバー '<interfacename1>' とインターフェイス '<defaultpropertyname>' の '<interfacename2>' との間で不適切です。
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 5f058c8e7d480b9145452ae85f186a6ac2ed0d56
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836351"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>Default プロパティ アクセスは継承インターフェイス メンバーの間であいまいな\<defaultpropertyname >' のインターフェイス '\<interfacename1 >' と'\<defaultpropertyname >' のインターフェイス '\<interfacename2 >'
インターフェイスは、同じ名前の既定プロパティを宣言するそれぞれの 2 つのインターフェイスから継承します。 コンパイラは、この既定のプロパティを修飾なしに、アクセスを解決できません。 次に例を示します。  
  
```  
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
  
 指定すると`testObj(1)`コンパイラは既定のプロパティに解決しようとしています。 ただし、2 つ可能な既定プロパティは、継承のインターフェイスにより、コンパイラは、このエラーを通知するためです。  
  
 **エラー ID:** BC30686  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   同じ名前のメンバーを継承しないようにします。 前の例では場合、`testObj`のメンバーのいずれかの必要はありません、たとえば、 `Iface2`、次のように宣言します。  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     - または -  
  
-   クラスで継承するインターフェイスを実装します。 これらの異なる名前を持つ継承されたプロパティを実装できます。 ただし、それらの 1 つだけでは、実装するクラスの既定のプロパティがあります。 次に例を示します。  
  
    ```  
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
