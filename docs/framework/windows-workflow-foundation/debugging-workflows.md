---
title: デバッグのワークフロー
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 17cee1f1b509e777edd3f08c55d473d768b19b55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945874"
---
# <a name="debugging-workflows"></a>デバッグのワークフロー
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、開発環境から実行中のワークフローをデバッグするオプションがいくつかあります。 ワークフローは、デザイナー、XAML、およびコードでデバッグできます。  
  
## <a name="debugging-in-the-workflow-designer"></a>ワークフロー デザイナーでのデバッグ  
 アクティビティを強調表示し、キーを押すか、ワークフロー デザイナーでアクティビティにブレークポイントを設定できます**F9**アクティビティのコンテキスト メニューを使用します。 ワークフロー ホストをデバッグ モードで実行すると、ワークフローの実行は一時停止します。 次のスクリーンショットでは、ワークフローの実行はブレークポイントで一時停止します。 詳細については、次を参照してください。[ワークフロー デザイナーでワークフローをデバッグ](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer)します。  
  
## <a name="debugging-in-xaml"></a>XAML でのデバッグ  
 デザイナーでワークフローがブレークポイントで一時停止すると、XAML でもワークフローをデバッグできます。 XAML での実行ポイントを表示する選択**XAML ビュー**ワークフローの実行が一時停止すると、ワークフロー デザイナーでします。 デバッグをデザイナーに切り替えるには、ソリューション エクスプローラーからデザイナーでワークフローを開き直します。 詳細については、「[方法 :ワークフロー デザイナーで XAML をデバッグ](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer)します。  
  
## <a name="debugging-in-code"></a>コードでのデバッグ  
 コードのブレークポイントは、他の命令型アプリケーションで使用する方法と同様に [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] で使用できます。 コードのブレークポイントを作成するコード ウィンドウの左端の余白をクリックします。 またはキーを押します**F9**カーソル位置にブレークポイントを配置します。  
  
## <a name="attaching-to-a-workflow-process"></a>ワークフロー プロセスへのアタッチ  
 ワークフローのデバッグは、Visual Studio のインフラストラクチャを使用したプロセスへのアタッチもサポートしています。 そのため、ワークフロー作成者は、Internet Information Services (IIS) 7.0 など異なるホスト環境で実行されているワークフローをデバッグできます。  
  
## <a name="remote-debugging"></a>Remote Debugging  
 Windows Workflow Foundation (WF) のリモート デバッグは機能は他の Visual Studio コンポーネント用のリモート デバッグと同じです。 リモート デバッグの使用方法の詳細については、次を参照してください。[方法。リモート デバッグを有効にする](https://go.microsoft.com/fwlink/?LinkId=196257)します。  
  
> [!NOTE]
>  ワークフロー アプリケーションは、x86 を対象とする場合のアーキテクチャとし、リモート デバッグは機能しません、リモート コンピューターで Visual Studio がインストールされているか、ワークフロー アプリケーションのターゲットを変更しない限り、64 ビット オペレーティング システムを実行しているコンピューターでホストされます。**任意の CPU**します。  
  
## <a name="extending-the-workflow-debugging-service"></a>ワークフロー デバッグ サービスの拡張  
 ワークフロー デバッガー サービスは公開されるようになり、ホストを変更したデザイナーでのモニタリング、シミュレーション、デバッグなど、カスタム アプリケーションを作成するときに使用できます。 詳細については、「<xref:System.Activities.Presentation.Debug.DebuggerService>」を参照してください。
