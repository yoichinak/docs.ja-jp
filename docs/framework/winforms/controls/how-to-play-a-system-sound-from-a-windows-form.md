---
title: '方法: Windows フォームからシステム サウンドを再生します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing for system events
- playing sounds [Windows Forms], Windows Forms
- system sounds [Windows Forms], playing from Windows Forms
- playing sounds [Windows Forms], system
- SoundPlayer class [Windows Forms], system sounds
- sounds [Windows Forms], playing
- examples [Windows Forms], sounds
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
ms.openlocfilehash: b2ac6c4f2e3334a9b4c5ff4d2a6e31b6b9bf3673
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711230"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a>方法: Windows フォームからシステム サウンドを再生します。
実行時に `Exclamation` システム サウンドを再生するコード例を次に示します。 システムが出す音の詳細については、<xref:System.Media.SystemSounds>を参照してください。  
  
## <a name="example"></a>例  
  
```vb  
Public Sub PlayExclamation()  
    SystemSounds.Exclamation.Play()  
End Sub  
```  
  
```csharp  
public void playExclamation()  
{  
    SystemSounds.Exclamation.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   <xref:System.Media?displayProperty=nameWithType> 名前空間への参照  
  
## <a name="see-also"></a>関連項目
- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [方法: Windows フォームからビープ音を再生します。](how-to-play-a-beep-from-a-windows-form.md)
- [方法: Windows フォームからサウンドを再生します。](how-to-play-a-sound-from-a-windows-form.md)
