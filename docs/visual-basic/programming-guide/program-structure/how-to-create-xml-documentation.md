---
title: '方法: Visual Basic で XML ドキュメントを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 9380c23ab6cfdbecd519926229b45ed863f07f9e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947716"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>方法: Visual Basic で XML ドキュメントを作成する
この例では、XML ドキュメントコメントをコードに追加する方法を示します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>型またはメンバーの XML ドキュメントを作成するには  
  
1. **コードエディター**で、ドキュメントを作成する型またはメンバーの上の行にカーソルを置きます。  
  
2. 「 `'''` 」と入力します (3 つの単一引用符)。  
  
     型またはメンバーの XML スケルトンが**コードエディター**に追加されます。  
  
3. 適切なタグの間に説明情報を追加します。  
  
    > [!NOTE]
    > XML ドキュメントブロック内に行を追加する場合、各行はで`'''`始まる必要があります。  
  
4. 新しい XML ドキュメントコメントと共に型またはメンバーを使用するコードを追加します。  
  
     IntelliSense では、型また\<はメンバーの概要 > タグのテキストが表示されます。  
  
5. コードをコンパイルして、ドキュメントコメントを含む XML ファイルを生成します。 詳細については、「[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XML の使用によるコードのドキュメントの作成](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
