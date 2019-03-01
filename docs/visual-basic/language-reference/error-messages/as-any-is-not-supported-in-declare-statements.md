---
title: "'As Any' は、'Declare' ステートメントではサポートされていません。"
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: b3fb3f208f3396f454388ec0c10406815fa957d8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974797"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a>'As Any' は、'Declare' ステートメントではサポートされていません。
`Any`データ型の併用`Declare`ステートメントでは、あらゆる種類のデータを含む可能性のある引数の使用を許可するには、Visual Basic 6.0 と以前のバージョン。 オーバー ロード、ただし、Visual Basic は、そのにより、`Any`データ型の廃止されています。  
  
 **エラー ID:** BC30828  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  を使用する特定の型のパラメーターを宣言します。例えば。  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2.  使用して、<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性を指定する`As Any`とき`Void*`によって呼び出されるプロシージャが必要です。  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [チュートリアル: Windows API の呼び出し](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
- [マネージド コードでのプロトタイプの作成](../../../framework/interop/creating-prototypes-in-managed-code.md)
