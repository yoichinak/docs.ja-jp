---
title: '方法: バックグラウンド操作を使用するフォームを実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: 98d51f9c6465186e77784aba080130110545f399
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192161"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>方法: バックグラウンド操作を使用するフォームを実装する
次のサンプル プログラムは、フィボナッチの数列を計算するフォームを作成します。 計算では、ユーザー インターフェイス スレッドとは別にあるスレッドで実行されるので、ユーザー インターフェイスは引き続き、計算の進行に伴う遅延なしに実行されます。  
  
 Visual Studio では、このタスクに対する広範なサポートが用意されています。  
  
 参照してください[チュートリアル。バック グラウンド操作を使用するフォームを実装する](walkthrough-implementing-a-form-that-uses-a-background-operation.md)します。  
  
## <a name="example"></a>例  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual C# の構築方法の詳細については、[、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
> [!CAUTION]
>  どのような種類のマルチスレッドを使用している場合でも、非常に深刻で複雑なバグを引き起こしてしまう可能性があります。 マルチスレッドを使用するソリューションを実装する前に、「[マネージド スレッド処理の実施](../../../standard/threading/managed-threading-best-practices.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [イベントベースの非同期パターンの概要](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [マネージド スレッド処理の実施](../../../standard/threading/managed-threading-best-practices.md)
