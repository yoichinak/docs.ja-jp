---
title: '方法: 変数 (Visual Basic) の可用性を制御します。'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 419f3eed30a5d4b35bcb9dde5242b9092ee9cb79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610500"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>方法: 変数 (Visual Basic) の可用性を制御します。
指定することで、変数の可用性を制御するその*アクセス レベル*します。 どのようなコードは、変数に対する読み取りまたは書き込み権限を持つアクセス レベルを決定します。  
  
- *メンバー変数*(モジュール レベルで、プロシージャの外に定義された) 既定でパブリック アクセスは、表示できるすべてのコードがアクセスできることを意味します。 これは、アクセス修飾子を指定することで変更できます。  
  
- *ローカル変数*(プロシージャの内部で定義されている)、プロシージャ内のコードだけがアクセスできますが、パブリック アクセスがあるとします。 ローカル変数のアクセス レベルを変更することはできませんが、それを含むプロシージャのアクセス レベルを変更できます。  
  
 詳細については、[ Visual Basic のアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
## <a name="private-and-public-access"></a>プライベートおよびパブリックのアクセス  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>変数をそのモジュール、クラスまたは構造内からのみアクセスできるようにするには  
  
1. 場所、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)モジュール、クラス、または構造体の内部では、プロシージャの外部の変数。  
  
2. 含める、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード、`Dim`ステートメント。  
  
     読み取りまたはからではなくが、モジュール、クラス、または構造内で任意の場所から変数への書き込みができる外です。  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>変数を参照できる任意のコードからアクセスできるようにするには  
  
1. メンバー変数では、配置、`Dim`変数ではなく、プロシージャの外部モジュール、クラス、または構造体には、内部のステートメント。  
  
2. 含める、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)キーワード、`Dim`ステートメント。  
  
     読み取りまたはアセンブリと同時に使用する任意のコードから、変数に書き込むことができます。  
  
 - または -  
  
1. ローカル変数では、配置、`Dim`プロシージャ内にある変数のステートメント。  
  
2. 含めないでください、`Public`キーワード、`Dim`ステートメント。  
  
     読み取りまたはからは、プロシージャ内で任意の場所から変数への書き込みができる外です。  
  
## <a name="protected-and-friend-access"></a>保護されているとフレンド アクセス  
 変数をクラスおよび派生クラス、またはそのアセンブリへのアクセス レベルを制限することができます。 同じアセンブリ内の他の場所または任意の派生クラスでは、コードからアクセスを許可するこれらの制限の和集合を指定することもできます。 結合することでこの和集合を指定する、`Protected`と`Friend`同じ宣言内のキーワード。  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>変数をそのクラスと派生クラス内からのみアクセスできるようにするには  
  
1. 場所、`Dim`変数、クラス内では、プロシージャの外側のステートメント。  
  
2. 含める、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)キーワード、`Dim`ステートメント。  
  
     読み取りまたはからではなくが、それから派生したあらゆるクラス内からだけでなく、クラス内で任意の場所から変数への書き込みができる派生チェーン内のクラス外です。  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>変数を同じアセンブリ内からのみアクセスできるようにするには  
  
1. 場所、`Dim`変数ではなく、プロシージャの外部モジュール、クラス、または構造体には、内部のステートメント。  
  
2. 含める、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)キーワード、`Dim`ステートメント。  
  
     読み取りまたは、モジュール、クラス、または構造内で任意の場所だけでなく、コードからは、同じアセンブリ内から変数への書き込みができるアセンブリの外側です。  
  
## <a name="example"></a>例  
 次の例では、変数の宣言`Public`、 `Protected`、 `Friend`、 `Protected Friend`、および`Private`アクセス レベル。 その場合、`Dim`ステートメントが、アクセス レベルを指定しますを含める必要はありません、`Dim`キーワード。  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 制限の厳しいアクセス レベルで変数をその悪意のあるコードが不正に、小さい方の可能性を使用して、します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../../visual-basic/language-reference/modifiers/private.md)
