---
title: シャドウとオーバーライドの違い (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: b935184f0e4d0378bfea69811aa4e6c068a9776f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827927"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>シャドウとオーバーライドの違い (Visual Basic)
基本クラスから継承するクラスを定義するときに場合がありますを 1 つまたは複数の派生クラスで基底クラスの要素を再定義します。 シャドウとオーバーライドは、この目的のためです。  
  
## <a name="comparison"></a>条件式  
 派生クラスは基底クラスから継承し、1 つの宣言された要素と他の再定義、シャドウとオーバーライドの両方が使用します。 2 つの重要な違いがあります。  
  
 次の表では、シャドウとオーバーライドを比較します。  
  
||||  
|---|---|---|  
|比較のポイント|シャドウ|オーバーライドします。|  
|目的|派生クラスで既に定義しているメンバーを導入する後続の基本クラスの変更に対する保護します。|プロシージャまたは同じの呼び出し元のシーケンスのプロパティの別の実装を定義することでポリモーフィズムを実現する<sup>1</sup>|  
|再定義された要素|いずれかの宣言された要素型|手順を示します (`Function`、 `Sub`、または`Operator`) またはプロパティ|  
|再定義する要素|いずれかの宣言された要素型|プロシージャまたは同一呼び出し元のシーケンスのプロパティのみ<sup>1</sup>|  
|再定義する要素のアクセス レベル|任意のアクセス レベル|上書きされた要素のアクセス レベルを変更することはできません。|  
|読みやすさと再定義する要素の書き込みの許可|任意の組み合わせ|読みやすさやすさのオーバーライドされたプロパティを変更することはできません。|  
|再定義の制御します。|基本クラスの要素は、強制またはシャドウを禁止することはできません。|基本クラスの要素を指定できます`MustOverride`、 `NotOverridable`、または `Overridable`|  
|キーワードの使用状況|`Shadows` 派生クラスではお勧めします。`Shadows`どちらでもない場合を想定`Shadows`も`Overrides`指定<sup>2</sup>|`Overridable` または`MustOverride`基本クラスでは必要です`Overrides`派生クラスで必要です|  
|派生クラスから派生するクラスで再定義する要素の継承|継承された要素をシャドウするさらに派生クラスです。シャドウされた要素を非表示のまま<sup>3</sup>|継承された要素をオーバーライドするさらに派生クラスです。上書きされた要素がまだオーバーライド|  
  
 <sup>1</sup> 、*シーケンスを呼び出す*要素の型から成る (`Function`、 `Sub`、 `Operator`、または`Property`)、パラメーター リストの名前し、型を返します。 プロパティ、またはその逆を持つプロシージャをオーバーライドすることはできません。 1 つの種類のプロシージャをオーバーライドすることはできません (`Function`、 `Sub`、または`Operator`) を別の種類。  
  
 <sup>2</sup>いずれかを指定しない場合`Shadows`または`Overrides`コンパイラが再定義の種類を使用することを確認させるために警告メッセージを発行します。 警告を無視する場合は、シャドウ機構が使用されます。  
  
 <sup>3</sup>シャドウ シャドウする要素がさらに派生クラスでアクセスできない場合は継承されません。 シャドウの要素として宣言した場合など、 `Private`、派生クラスから派生するクラスが要素ではなく元の要素を継承します。  
  
## <a name="guidelines"></a>ガイドライン  
 通常、次の場合にオーバーライドする使用します。  
  
-   ポリモーフィックな派生クラスを定義します。  
  
-   安全のために、コンパイラが、同一の要素型と呼び出し元の順序を適用します。  
  
 通常、シャドウ次の場合に使用します。  
  
-   予想される基底クラスが変更される可能性があるし、他の人と同じ名前を使用して要素を定義します。  
  
-   要素の型を変更またはシーケンスを呼び出す必要です。  
  
## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [方法: 変数と同じ名前の変数を非表示にします。](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [方法: 継承された変数を非表示にします。](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [方法: 派生クラスによって非表示に変数にアクセスします。](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
