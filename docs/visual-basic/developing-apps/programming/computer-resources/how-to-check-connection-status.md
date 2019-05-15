---
title: '方法: Visual Basic で接続ステータスをチェックする'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 1a03b181c2e363c3380c4f9858b629713641f2c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620676"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a>方法: Visual Basic で接続ステータスをチェックする
正常に動作しているネットワーク接続またはインターネット接続がコンピューターにあるかどうかは、<xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> プロパティを使って調べることができます。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a>正常に動作している接続がコンピューターにあるかどうかを調べるには  
  
- `IsAvailable` プロパティが `True` であるか `False` であるかを調べます。 このプロパティのステータスを調べて報告するコードを次に示します。  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     このコード例は、IntelliSense コード スニペットとしても利用できます。 コード スニペット ピッカーでは、これは **[接続とネットワーク]** にあります。 詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
