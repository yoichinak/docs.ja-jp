---
title: '方法: Windows フォームからビープ音を再生します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
ms.openlocfilehash: d04bf4bd45aa6ba5dfe231d5f69c2b2a13765373
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710434"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>方法: Windows フォームからビープ音を再生します。
実行時にビープ音を再生する例を次に示します。  
  
## <a name="example"></a>例  
  
```vb  
Public Sub OnePing()  
    Beep()  
End Sub  
```  
  
```csharp  
public void onePing()  
{  
    SystemSounds.Beep.Play();  
}  
```  
  
> [!NOTE]
>  再生されるサウンド、C#コード サンプルはによって決定されます、<xref:System.Media.SystemSounds.Beep%2A>システム サウンド設定します。 詳細については、「 <xref:System.Media.SystemSounds> 」を参照してください。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 C#、この例への参照が必要です、<xref:System.Media?displayProperty=nameWithType>名前空間。  
  
## <a name="see-also"></a>関連項目
- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [方法: Windows フォームからシステム サウンドを再生します。](how-to-play-a-system-sound-from-a-windows-form.md)
- [方法: Windows フォームからサウンドを再生します。](how-to-play-a-sound-from-a-windows-form.md)
