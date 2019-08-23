---
title: Mid ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963552"
---
# <a name="mid-statement"></a>Mid ステートメント
`String`変数内の指定された数の文字を別の文字列の文字に置き換えます。  
  
## <a name="syntax"></a>構文  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>指定項目  
 `Target`  
 必須。 変更する`String`変数の名前。  
  
 `Start`  
 必須。 `Integer`条件. テキストの置換`Target`を開始する位置の文字位置。 `Start`1から始まるインデックスを使用します。  
  
 `Length`  
 任意。 `Integer`条件. 置換する文字数。 省略した場合`String`は、すべてが使用されます。  
  
 `StringExpression`  
 必須。 `String`の`Target`一部を置換する式。  
  
## <a name="exceptions"></a>例外  
  
|例外の型|条件|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`< = 0 また`Length`は < 0 です。|  
  
## <a name="remarks"></a>Remarks  
 置換される文字数は、常にの文字`Target`数以下です。  
  
 Visual Basic には<xref:Microsoft.VisualBasic.Strings.Mid%2A> 、関数`Mid`とステートメントがあります。 これらの要素は、どちらも文字列内の指定された文字数`Mid`に対して動作します`Mid`が、関数は、ステートメントが文字を置換する間、文字を返します。 詳細については、「 <xref:Microsoft.VisualBasic.Strings.Mid%2A> 」を参照してください。  
  
> [!NOTE]
> 以前のバージョンの Visual Basic のステートメントでは、文字ではなく、部分文字列がバイト単位で置き換えられます。`MidB` これは主に、2バイト文字セット (DBCS) アプリケーションで文字列を変換するために使用されます。 すべての Visual Basic 文字列は Unicode `MidB`形式であり、サポートされなくなりました。  
  
## <a name="example"></a>例  
 この例では`Mid` 、ステートメントを使用して、文字列変数内の指定された数の文字を別の文字列の文字に置き換えます。  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [Microsoft. Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **モジュール:** `Strings`  
  
 **組み立て**Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [文字列](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Visual Basic の文字列の概要](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
