---
title: アクセスするインスタンスがインターフェイス型であるため、遅延バインドされたオーバーロードの解決は '<procedurename>' に適用されません。
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 7f2ae3bb0e7c09d966c53fb17b1cbe675dfce8b9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814056"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a>遅延バインドされたオーバー ロードの解決には適用できません '\<procedurename >' へのアクセスのインスタンスがインターフェイス型であるため
オーバー ロードされたプロパティまたはプロシージャへの参照を解決するのには、コンパイラがしようとしていますが、型の引数であるため、参照が失敗した`Object`インターフェイスのデータ型であり、参照元オブジェクト。 `Object`引数は、遅延バインディングとして参照を解決するのには、コンパイラを強制します。  
  
 このような場合は、コンパイラを基になるインターフェイスを実装するクラスの代わりにオーバー ロードを解決します。 クラスには、オーバー ロードされたバージョンのいずれかが名前変更、コンパイラはその名前が異なるため、オーバー ロードするには、そのバージョンを考慮しません。 これで、コンパイラは参照を解決するのには、適切な選択されている可能性があるときに名前を変更したバージョンを無視します。  
  
 **エラー ID:** BC30933  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   使用`CType`から引数をキャストする`Object`呼び出そうとするオーバー ロードのシグネチャで指定された型にします。  
  
     基になるインターフェイスを参照しているオブジェクトをキャストする役立ちませんに注意してください。 このエラーを回避するために引数をキャストする必要があります。  
  
## <a name="example"></a>例  
 次の例は、オーバー ロードされた呼び出し`Sub`コンパイル時にこのエラーが発生するプロシージャ。  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 コンパイラへの呼び出しを許可されている場合、前の例で`s1`が書き込まれると、解決が行わクラスを通じて`c1`インターフェイスではなく`i1`します。 つまり、コンパイラは見なしません`s2`その名前が異なるため、`c1`は適切な選択であるで定義されている場合でも、`i1`します。  
  
 次のコード行のいずれかへの呼び出しを変更することで、エラーを修正できます。  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 前の行のコードに明示的にキャスト、`Object`変数`o1`オーバー ロードは、定義されているパラメーターの型のいずれかにします。  
  
## <a name="see-also"></a>関連項目

- [プロシージャのオーバーロード](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [オーバーロードの解決](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)
