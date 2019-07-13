---
title: Windows フォーム コントロールのマルチスレッド処理
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cc7f358a62c8057abb77e1f5a28544bb6c858d98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012725"
---
# <a name="multithreading-in-windows-forms-controls"></a>Windows フォーム コントロールのマルチスレッド処理
多くのアプリケーションで行うことができます、ユーザー インターフェイス (UI) の高い別のスレッドで時間のかかる操作を実行することによって。 多数のツールがあるマルチ スレッドなど、Windows フォーム コントロール、<xref:System.Threading>名前空間、<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>メソッド、および`BackgroundWorker`コンポーネント。  
  
> [!NOTE]
>  `BackgroundWorker`コンポーネントが置換および機能を追加、<xref:System.Threading>名前空間と<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>メソッドです。 ただし、これらは保持されます下位互換性と将来の使用を選択した場合。 詳細については、次を参照してください。 [BackgroundWorker コンポーネントの概要](backgroundworker-component-overview.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: Windows フォーム コントロールのスレッド セーフな呼び出しを行う](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Windows フォーム コントロールをスレッド セーフな呼び出しを作成する方法を紹介します。  
  
 [方法: ファイルを検索するバック グラウンド スレッドを使用して、](how-to-use-a-background-thread-to-search-for-files.md)  
 使用する方法を示しています、<xref:System.Threading>名前空間と<xref:System.Windows.Forms.Control.BeginInvoke%2A>メソッドを非同期的にファイルを検索します。  
  
## <a name="reference"></a>参照  
 <xref:System.ComponentModel.BackgroundWorker>  
 非同期操作のワーカー スレッドをカプセル化するコンポーネントについて説明します。  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 サウンドを非同期的に読み込む方法について説明します。  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 イメージを非同期的に読み込む方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [方法: バックグラウンドで操作を実行する](how-to-run-an-operation-in-the-background.md)  
 時間のかかる操作を行う方法を示しています、<xref:System.ComponentModel.BackgroundWorker>コンポーネント。  
  
 [BackgroundWorker コンポーネントの概要](backgroundworker-component-overview.md)  
 使用する方法について説明するトピックを示します、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの非同期操作をします。
