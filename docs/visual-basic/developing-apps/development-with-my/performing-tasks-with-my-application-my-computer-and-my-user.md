---
title: My.Application、My.Computer、および My.User でのタスクの実行 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 0372fbf63f6d12e266674f92225183911aa4ca30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834050"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>My.Application、My.Computer、および My.User でのタスクの実行 (Visual Basic)
次の 3 つの中央`My`と一般的な情報へのアクセスで使用される機能を提供するオブジェクトが`My.Application`(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>)、 `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)、および`My.User`(<xref:Microsoft.VisualBasic.ApplicationServices.User>)。 これらのオブジェクトを使用して、それぞれ、現在のアプリケーションや、アプリケーションがインストールされているコンピューター、アプリケーションの現在のユーザーに関連する情報にアクセスすることができます。  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My.Application、My.Computer、および My.User  
 次の例の情報をする方法を使用して取得`My`します。  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 情報を取得するだけでなくこれら 3 つのオブジェクトを通じて公開されるメンバーをすることもそのオブジェクトに関連するメソッドを実行します。 たとえば、さまざまなファイルを操作または経由でのレジストリを更新する方法をアクセスできる`My.Computer`します。  
  
 簡単かつ迅速で、ファイル I/O が大幅に`My`さまざまなメソッドとファイル、ディレクトリ、およびドライブを操作するためのプロパティが含まれています。 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>オブジェクトは、大きな構造化されたファイルが区切られた、または固定幅フィールドから読み取ることができます。 この例を開いて、 `TextFieldParser` `reader`オブジェクトからの読み取りを使用して`C:\TestFolder1\test1.txt`します。  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application` アプリケーションのカルチャを変更することができます。 次の例では、このメソッドを呼び出す方法を示します。  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [プロジェクトの種類に応じた My の機能](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
