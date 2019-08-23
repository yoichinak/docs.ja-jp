---
title: '方法: Windows フォームからビープ音を再生する'
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
ms.openlocfilehash: 1a72f88c05fb21c11864058ffbe81c1957525375
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966511"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>方法: Windows フォームからビープ音を再生する
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
> C#コードサンプルで再生されるサウンドは、 <xref:System.Media.SystemSounds.Beep%2A>システムサウンド設定によって決まります。 詳細については、「 <xref:System.Media.SystemSounds> 」を参照してください。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 のC#場合、この例では<xref:System.Media?displayProperty=nameWithType>名前空間への参照が必要です。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [方法: Windows フォームからシステムサウンドを再生する](how-to-play-a-system-sound-from-a-windows-form.md)
- [方法: Windows フォームからサウンドを再生する](how-to-play-a-sound-from-a-windows-form.md)
