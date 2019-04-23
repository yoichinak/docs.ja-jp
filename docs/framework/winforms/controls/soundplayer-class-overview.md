---
title: SoundPlayer クラスの概要
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 3ff23cbfa78b803d4526e7a7c389fd5d458a967c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195008"
---
# <a name="soundplayer-class-overview"></a>SoundPlayer クラスの概要
<xref:System.Media.SoundPlayer> クラスを使用すると、アプリケーションにサウンドを簡単に組み込むことができます。  
  
 <xref:System.Media.SoundPlayer>クラスは、リソースまたは UNC や HTTP の場所からの .wav 形式のサウンド ファイルを再生できます。 さらに、<xref:System.Media.SoundPlayer>クラスでは、読み込みまたは非同期的にサウンドを再生することができます。  
  
 <xref:System.Media.SystemSounds> クラスを使用して、ビープ音を含む、共通のシステム サウンドを再生することもできます。  
  
## <a name="commonly-used-properties-methods-and-events"></a>一般的に使用されるプロパティ、メソッド、およびイベント  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> プロパティ|サウンドのファイル パスまたは Web アドレスです。 使用可能な値には UNC または HTTP があります。|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> プロパティ|プログラムが、例外をスローする前にサウンドの読み込みを待機するミリ秒単位の時間です。 既定値は 10 秒です。|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> プロパティ|サウンドの読み込みが終了したかどうかを示すブール値です。|  
|<xref:System.Media.SoundPlayer.Load%2A> メソッド|サウンドを同期的に読み込みます。|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> メソッド|サウンドの非同期的な読み込みを開始します。 読み込みが完了したら、生成、<xref:System.Media.SoundPlayer.OnLoadCompleted%2A>イベント。|  
|<xref:System.Media.SoundPlayer.Play%2A> メソッド|指定されたサウンドを再生、<xref:System.Media.SoundPlayer.SoundLocation%2A>または<xref:System.Media.SoundPlayer.Stream%2A>新しいスレッドのプロパティ。|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> メソッド|指定されたサウンドを再生、<xref:System.Media.SoundPlayer.SoundLocation%2A>または<xref:System.Media.SoundPlayer.Stream%2A>プロパティ、現在のスレッドにします。|  
|<xref:System.Media.SoundPlayer.Stop%2A> メソッド|現在再生されているサウンドを停止します。|  
|<xref:System.Media.SoundPlayer.LoadCompleted> イベント|サウンドの読み込みが試みられた後に発生します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
