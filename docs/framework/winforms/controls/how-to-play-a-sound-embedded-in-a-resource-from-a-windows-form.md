---
title: '方法: Windows フォームからリソースに埋め込まれたサウンドを再生する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
ms.openlocfilehash: 49235f9cb035c5a09c26b427f855fc00e818fe1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078578"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>方法: Windows フォームからリソースに埋め込まれたサウンドを再生する
使用することができます、<xref:System.Media.SoundPlayer>埋め込みリソースからサウンドを再生するクラス。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
 インポート、<xref:System.Media?displayProperty=nameWithType>名前空間。  
  
 サウンド ファイルを、埋め込まれたリソースとしてプロジェクトに取り込み。  
  
 "\<AssemblyName>" を、サウンド ファイルが埋め込まれているアセンブリの名前に置換。 ".dll" というサフィックスは含めないでください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Media.SoundPlayer>
- [方法: Windows フォームからサウンドを再生します。](how-to-play-a-sound-from-a-windows-form.md)
- [方法: Windows フォームで再生するサウンドをループします。](how-to-loop-a-sound-playing-on-a-windows-form.md)
