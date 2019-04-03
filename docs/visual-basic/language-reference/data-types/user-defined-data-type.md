---
title: ユーザー定義データ型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 5fe12d18c7f403c1a50ed548a260ba39e83280eb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814199"
---
# <a name="user-defined-data-type"></a>ユーザー定義型
定義する形式でデータを保持します。 `Structure`ステートメントの形式を定義します。  
  
 以前のバージョンの Visual Basic では、ユーザー定義型 (UDT) をサポートします。 現在のバージョンの展開に UDT を*構造*します。 構造体は 1 つまたは複数の連結*メンバー*さまざまなデータ型。 Visual Basic では、個別にそのメンバーをアクセスすることもできます。 ただし、1 つの単位として構造体が扱われます。  
  
## <a name="remarks"></a>Remarks  
 定義し、構造体のデータ型を使用して、1 つの単位にさまざまなデータ型を結合する必要がある場合、または基本データ型のいずれもニーズに対応します。  
  
 構造体のデータ型の既定値は、各メンバーの既定値の組み合わせで構成されます。  
  
## <a name="declaration-format"></a>宣言の形式  
 構造体の宣言が始まり、 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)で終わると、`End Structure`ステートメント。 `Structure`ステートメントは、これは、構造体を定義するデータ型の識別子でも構造体の名前を提供します。 コードの他の部分では、変数、パラメーター、および関数は、この構造体のデータ型の値を返すを宣言するのに、この識別子を使用できます。  
  
 宣言、`Structure`と`End Structure`ステートメントでは、構造体のメンバーを定義します。  
  
## <a name="member-access-levels"></a>メンバーのアクセス レベル  
 使用してすべてのメンバーを宣言する必要があります、 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)またはなど、アクセス レベルを指定するステートメント[パブリック](../../../visual-basic/language-reference/modifiers/public.md)、[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)、または[プライベート](../../../visual-basic/language-reference/modifiers/private.md). 使用する場合、`Dim`ステートメントでは、パブリックにアクセス レベルの既定値。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **メモリ使用量。**  他のすべての複合データ型と同様に、構造体の総メモリ使用量を計算する場合、各メンバーのストレージ割り当ての公称サイズを単に合計しただけでは安全ではありません。 さらに、メモリ内に格納される順序が宣言の順序と同じであると仮定するのも安全ではありません。 構造体のストレージ レイアウトを制御する必要がある場合は、<xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性を `Structure` ステートメントに適用します。  
  
-   **相互運用の考慮事項。** オートメーションまたは COM オブジェクトなどの .NET Framework 用に作成されていないコンポーネントをやり取りする場合、他の環境でのユーザー定義型は Visual Basic 構造型と互換性がないことに注意してください。  
  
-   **拡大します。** 任意の構造のデータ型との間の自動変換はありません。 変換演算子を定義するには構造体を使用して、 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)、するには、各変換演算子を宣言して`Widening`または`Narrowing`します。  
  
-   **型宣言文字。** リテラルの型文字または識別子の型文字は、構造体のデータ型はあるありません。  
  
-   **フレームワークの型。** .NET Framework では、対応する型はありません。 すべての構造は、.NET Framework クラスから継承<xref:System.ValueType?displayProperty=nameWithType>に対応する個別の構造体がありませんが、<xref:System.ValueType?displayProperty=nameWithType>します。  
  
## <a name="example"></a>例  
 構造体の宣言の概要を次に示します。  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
