---
title: '方法: My Documents ディレクトリの内容を取得する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: fe98d3e92726dc6c4ed576ef989d968852c846d6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821830"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>方法: My Documents ディレクトリの内容を取得する (Visual Basic)
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> オブジェクトを使用すると、**My Documents** や **Desktop** など、多くの **All Users** ディレクトリを読み取ることができます。  
  
### <a name="to-read-from-the-my-documents-folder"></a>My Documents フォルダーを読み取るには  
  
-   `ReadAllText` メソッドを使用して、指定したディレクトリの各ファイルからテキストを読み取ります。 次のコードでは、ディレクトリとファイルを指定し、`ReadAllText` を使用して、`patients` という名前の文字列に読み取ります。  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
