---
title: My.Resources と My.Settings による Rapid Application Development (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 1d5fe35ea491c2c2d3de82ef208fec59a6079a25
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976071"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>My.Resources と My.Settings による Rapid Application Development (Visual Basic)
`My.Resources`オブジェクトは、アプリケーションのリソースへのアクセスを提供し、アプリケーションのリソースを動的に取得することができます。  
  
## <a name="retrieving-resources"></a>リソースの取得  
 多数のオーディオ ファイル、アイコン、イメージ、および文字列などのリソースを使用して取得できる、`My.Resources`オブジェクト。 たとえば、アプリケーションのカルチャ固有のリソース ファイルにアクセスすることができます。 次の例では、フォームのアイコンを設定するという名前のアイコン`Form1Icon`アプリケーションのリソース ファイルに格納します。  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 `My.Resources`オブジェクトはグローバル リソースのみを公開します。 フォームに関連付けられているリソース ファイルへのアクセスは行いません。 フォームのフォーム リソースにアクセスする必要があります。  
  
 同様に、`My.Settings`オブジェクトは、アプリケーションの設定へのアクセスを提供し、動的に格納し、プロパティの設定と、アプリケーションの他の情報を取得することができます。 詳細については、次を参照してください。 [My.Resources オブジェクト](../../../visual-basic/language-reference/objects/my-resources-object.md)と[My.Settings オブジェクト](../../../visual-basic/language-reference/objects/my-settings-object.md)します。  
  
## <a name="see-also"></a>関連項目
- [My.Resources オブジェクト](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [My.Settings オブジェクト](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [アプリケーション設定へのアクセス](../../../visual-basic/developing-apps/programming/app-settings/index.md)
