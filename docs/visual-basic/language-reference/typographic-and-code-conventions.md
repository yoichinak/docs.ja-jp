---
title: 表記規則とコード規則 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: c915d12fa633ec2f95cd82d5f795d48d0f551662
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604120"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>表記規則とコード規則 (Visual Basic)
Visual Basic のドキュメントでは、次の表記規則とコード規則に従って記述されています。  
  
## <a name="typographic-conventions"></a>表記規則  
  
|例|説明|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Visual Basic 特有のキーワードやランタイム メンバは、太字で先頭を大文字にして表記します。|  
|**SmallProject**, **ButtonCollection**|この例で示すように、単語や語句を入力するように指示されますが書式設定します。|  
|[Module ステートメント](../../visual-basic/language-reference/statements/module-statement.md)|この例で示すように、リンクをクリックすると、別のヘルプ ページに移動できますが書式設定します。|  
|*object*, *variableName*, `argumentList`|この例で示すように入力する情報のプレース ホルダーは書式設定されます。|  
|[ Shadows ], [ *expressionList* ]|構文では、省略可能な項目は、角かっこで囲まれます。|  
|{ `Public` &#124; `Friend` &#124; `Private` }|構文では、2 つ以上の項目間の選択を行う必要がある場合は、項目が中かっこで囲まれているし、縦棒で区切られました。<br /><br /> 1 と 1 つだけ、項目を選択する必要があります。|  
|[ `Protected` &#124; `Friend` ]|構文では、2 つ以上の項目間を選択するオプションがある場合は、アイテムが角かっこで囲まれているし、縦棒で区切られました。<br /><br /> 項目の任意の組み合わせまたは項目を選択できません。|  
|[{ `ByVal` &#124; `ByRef` }]|構文は複数の項目を選択することができますが、完全には、アイテムを省略することもできます。 項目は中かっこで囲まれ、縦棒で区切られた、角かっこで囲みます。|  
|*memberName*1、 *memberName*2、 *memberName*3|例で示すように、添字によって同じプレース ホルダーの複数のインスタンスが区別されます。|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|構文、省略記号 (...) で不特定数の省略記号の直前の種類の項目を指定するためです。<br /><br /> コードでは、わかりやすく説明を省略するとコードを示します。|  
|ESC キーを入力します|キー名と、キーボードのキー シーケンスは、すべて大文字で表示されます。|  
|ALT + F1|プラス記号 (+) は、キーの組み合わせを表します。 たとえば、Alt + F1 は Alt キーを押しながら、F1 キーを押すことを表します。|  
  
## <a name="code-conventions"></a>コード規則  
  
|例|説明|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|コード サンプルでは、固定ピッチ フォントで表示され、は、この例で示すように書式設定します。|  
|前のステートメントの値を設定する`sampleString`に「こんにちは, world!」|説明のテキスト内のコード要素は、この例で示すように固定ピッチ フォントで表示されます。|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|アポストロフィ (') で、REM キーワードは、コードのコメントが導入されました。|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|空白と行の末尾にアンダー スコア (_) では、次の行にステートメントが続くことを示します。|  
  
## <a name="see-also"></a>関連項目
- [Visual Basic の言語リファレンス](../../visual-basic/language-reference/index.md)
- [キーワード](../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic ランタイム ライブラリのメンバー](../../visual-basic/language-reference/runtime-library-members.md)
- [Visual Basic の名前付け規則](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [方法: コード内でステートメントを分割および連結する](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [コード内のコメント](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
