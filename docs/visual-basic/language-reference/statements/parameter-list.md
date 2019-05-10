---
title: パラメーター リスト (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: e58d80896d11b4154c7197d4cdaf73a536fdd5e7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583550"
---
# <a name="parameter-list-visual-basic"></a>パラメーター リスト (Visual Basic)
プロシージャは呼び出された場合、パラメーターを指定します。 複数のパラメーターは、コンマで区切られます。 1 つのパラメーターの構文を次に示します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>指定項目  
 `attributelist`  
 任意。 このパラメーターに適用される属性の一覧です。 囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ ("`<`「と」`>`")。  
  
 `Optional`  
 任意。 プロシージャが呼び出されたときに、このパラメーターが必要ないことを指定します。  
  
 `ByVal`  
 任意。 プロシージャが置換または呼び出し元のコードに対応する引数の基になる変数の要素を再割り当てできませんを指定します。  
  
 `ByRef`  
 任意。 あるプロシージャ要素を変更できます、基になる変数呼び出し元のコードで呼び出し元コード自体と同じようを指定します。  
  
 `ParamArray`  
 任意。 パラメーター リストの最後のパラメーターが指定されたデータ型の要素の省略可能な配列であることを示します。 これには、呼び出し元のコード、プロシージャに任意の数の引数を渡すことができます。  
  
 `parametername`  
 必須。 パラメーターを表すローカル変数の名前です。  
  
 `parametertype`  
 場合に、必ず`Option Strict`は`On`します。 パラメーターを表すローカル変数のデータ型。  
  
 `defaultvalue`  
 必要な`Optional`パラメーター。 パラメーターのデータ型に評価される定数または定数式です。 型の場合`Object`、クラス、インターフェイス、配列、または構造体では、既定値を指定できますのみまたは`Nothing`します。  
  
## <a name="remarks"></a>Remarks  
 パラメーターはかっこで囲むし、コンマで区切られました。 任意のデータ型では、パラメーターを宣言することができます。 指定しない場合`parametertype`、既定値は`Object`します。  
  
 呼び出し元のコードはプロシージャを呼び出す際に渡して、*引数*必要な各パラメーターにします。 詳細については、次を参照してください。[の相違点の間でパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)します。  
  
 呼び出し元のコードは、各パラメーターに渡す引数は、呼び出し元のコード内の基になる要素へのポインターです。 この要素が場合*不変*(定数、リテラル、列挙型、または式)、すべてのコードを変更することはできません。 ある場合、*変数*要素 (宣言された変数、フィールド、プロパティ、配列の要素、または構造体の要素)、呼び出し元のコードを変更できます。 詳細については、次を参照してください。[変更の間の相違点と変更できない引数](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)します。  
  
 Variable 要素が渡された場合`ByRef`プロシージャがも変更できます。 詳細については、次を参照してください。[の相違点の間の値と参照渡しによって引数を渡す](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)します。  
  
## <a name="rules"></a>ルール  
  
- **かっこです。** パラメーター リストを指定する場合は、かっこで囲む必要があります。 パラメーターがない場合は、空のリストを囲むかっこを引き続き使用できます。 これにより、プロシージャに要素が明確にすることによって、コードの読みやすさが向上します。  
  
- **省略可能なパラメーター。** 使用する場合、`Optional`パラメーター修飾子の一覧ですべての後続のパラメーターはオプションもありを使用して宣言する、`Optional`修飾子。  
  
     すべての省略可能なパラメーター宣言を指定する必要があります、`defaultvalue`句。  
  
     詳細については、次を参照してください。[省略可能なパラメーター](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)します。  
  
- **パラメーターの配列。** 指定する必要があります`ByVal`の`ParamArray`パラメーター。  
  
     両方を使用することはできません`Optional`と`ParamArray`パラメーター リストを同じにします。  
  
     詳細については、次を参照してください。[パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)します。  
  
- **値渡し。** すべての引数について既定のメカニズムは`ByVal`手順、つまり基になる可変要素を変更できません。 ただし、要素が参照型の場合は、プロシージャが変更できます内容や、基になるオブジェクトのメンバーでも交換や、オブジェクト自体を再割り当てはできません。  
  
- **パラメーター名。** 次のパラメーターのデータ型が配列の場合は、`parametername`かっこの直後にします。 パラメーター名の詳細については、次を参照してください。 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
## <a name="example"></a>例  
 次の例は、`Function`プロシージャを 2 つのパラメーターを定義します。  
  
 [!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [方法: コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
