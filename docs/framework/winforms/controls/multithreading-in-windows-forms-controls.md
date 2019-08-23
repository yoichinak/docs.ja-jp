---
title: Windows フォーム コントロールのマルチスレッド処理
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952679"
---
# <a name="multithreading-in-windows-forms-controls"></a>Windows フォーム コントロールのマルチスレッド処理
多くのアプリケーションでは、別のスレッドで時間のかかる操作を実行することで、ユーザーインターフェイス (UI) の応答性を高めることができます。 <xref:System.Threading>名前空間`BackgroundWorker` 、メソッド、コンポーネントなど、Windows フォームコントロールのマルチスレッドでは、さまざまなツールを使用できます。 <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>  
  
> [!NOTE]
> コンポーネント`BackgroundWorker`は、 <xref:System.Threading>名前空間と<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>メソッドに置き換えられ、機能を追加します。ただし、これらは下位互換性と将来の使用の両方のために保持されます (選択した場合)。 詳細については、「 [BackgroundWorker コンポーネントの概要](backgroundworker-component-overview.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: Windows フォームコントロールに対してスレッドセーフな呼び出しを行う](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Windows フォームコントロールに対してスレッドセーフな呼び出しを行う方法を示します。  
  
 [方法: バックグラウンドスレッドを使用してファイルを検索する](how-to-use-a-background-thread-to-search-for-files.md)  
 <xref:System.Threading>名前空間<xref:System.Windows.Forms.Control.BeginInvoke%2A>とメソッドを使用して、ファイルを非同期的に検索する方法を示します。  
  
## <a name="reference"></a>参照  
 <xref:System.ComponentModel.BackgroundWorker>  
 非同期操作のワーカースレッドをカプセル化するコンポーネントについて説明します。  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 サウンドを非同期に読み込む方法を説明します。  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 画像を非同期に読み込む方法を説明します。  
  
## <a name="related-sections"></a>関連項目  
 [方法: バックグラウンドで操作を実行する](how-to-run-an-operation-in-the-background.md)  
 <xref:System.ComponentModel.BackgroundWorker>コンポーネントで時間のかかる操作を実行する方法について説明します。  
  
 [BackgroundWorker コンポーネントの概要](backgroundworker-component-overview.md)  
 <xref:System.ComponentModel.BackgroundWorker>コンポーネントを非同期操作に使用する方法について説明するトピックを示します。
