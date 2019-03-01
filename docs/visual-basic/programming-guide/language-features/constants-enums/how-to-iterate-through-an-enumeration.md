---
title: '方法: Visual Basic で列挙型を反復処理します。'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: dd7a540839fd833d3a316506e433c576edae5384
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979087"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>方法: Visual Basic で列挙型を反復処理します。
一連の関連する定数を操作する場合や、定数値に名前を関連付ける場合は、列挙型を使うと便利です。 列挙体を反復処理に移動できますを使用して、配列に、<xref:System.Enum.GetValues%2A>メソッド。 使用して、列挙を反復処理することも、`For...Each`ステートメントを使用して、<xref:System.Enum.GetNames%2A>または<xref:System.Enum.GetValues%2A>文字列または数値の値を抽出するメソッド。  
  
### <a name="to-iterate-through-an-enumeration"></a>列挙体を反復処理するには  
  
-   配列を宣言しを使って、列挙型を変換、<xref:System.Enum.GetValues%2A>こととして、配列を渡す前にメソッドは、他の変数。 次の例は、列挙体の各メンバーを表示します。<xref:Microsoft.VisualBasic.FirstDayOfWeek>ように、列挙体で反復処理します。  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>関連項目
- [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [方法: 列挙体を宣言します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [方法: 列挙値に関連付けられている文字列を確認します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [方法: 列挙体のメンバーを参照してください。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
