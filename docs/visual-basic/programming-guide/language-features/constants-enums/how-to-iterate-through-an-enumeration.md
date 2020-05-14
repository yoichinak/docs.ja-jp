---
title: '方法: 列挙型を反復処理する'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 6e8fd6760565a73d9d3b3d1d02fc872992eea354
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354021"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>方法: Visual Basic で列挙型を反復処理する
一連の関連する定数を操作する場合や、定数値に名前を関連付ける場合は、列挙型を使うと便利です。 <xref:System.Enum.GetValues%2A> メソッドを使用して列挙型を配列に入れると、列挙型の反復処理を行うことができます。 また、`For...Each` ステートメント、<xref:System.Enum.GetNames%2A> メソッド、または <xref:System.Enum.GetValues%2A> メソッドを使用して列挙型の反復処理を行うと、文字列値または数値を抽出できます。  
  
### <a name="to-iterate-through-an-enumeration"></a>列挙型を反復処理するには  
  
- 他の変数の場合と同様に、配列を宣言して <xref:System.Enum.GetValues%2A> メソッドにより列挙型をその配列に変換してから、配列を渡します。 次の例では、列挙型 <xref:Microsoft.VisualBasic.FirstDayOfWeek> の反復処理の進捗に応じて、この列挙型の各メンバーが表示されます。  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>関連項目

- [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [方法: 列挙型を宣言する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [方法: 列挙値に関連付けられている文字列を確認する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [方法: 列挙型のメンバーを参照する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
