---
title: Visual Basic アプリケーション モデルの概要
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: 0144c92e01e617081ae05003e6a7175c63166891
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622793"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Visual Basic アプリケーション モデルの概要
Visual Basic Windows フォーム アプリケーションの動作を制御するための適切に定義されたモデルを提供します。 Visual Basic アプリケーション モデルです。 このモデルには、アプリケーションのスタートアップとシャット ダウン、だけでなくハンドルされない例外をキャッチのイベントを処理するためのイベントが含まれています。 単一インスタンス アプリケーションを開発するためのサポートも提供します。 アプリケーション モデルとは、拡張可能なため、詳細に制御を必要がある開発者はそのオーバーライド可能なメソッドをカスタマイズできます。  
  
## <a name="uses-for-the-application-model"></a>アプリケーション モデルの使用方法  
 一般的なアプリケーションを起動およびシャット ダウン時にタスクを実行する必要があります。 たとえば、起動時、アプリケーションことができますスプラッシュ スクリーンを表示、データベース接続を作成、保存済みの状態を読み込むおよび具合します。 アプリケーションがシャット ダウン時、データベース接続を閉じて、現在の状態を保存、具合およびできます。 さらに、アプリケーション コードを実行できます特定アプリケーションがシャット ダウンが予期せずに、このような未処理の例外時にします。  
  
 Visual Basic アプリケーション モデルでは、簡単に作成、*単一インスタンス*アプリケーション。 単一インスタンス アプリケーションは、コンピューターを一度に実行される通常のアプリケーションから、アプリケーションのインスタンスを 1 つだけは異なります。 単一インスタンスのアプリケーションの別のインスタンスを起動しようとすると、結果の通知を送信元のインスタンス: で、`StartupNextInstance`イベント-を別の起動しようとしました。 通知には、後続のインスタンスのコマンドライン引数が含まれています。 すべての初期化を行う前に、アプリケーションの後続のインスタンスが閉じられます。  
  
 単一インスタンス アプリケーションが起動し、最初のインスタンスまたは後続のアプリケーションのインスタンスがあるかどうかを確認します。  
  
- 最初のインスタンスの場合、通常どおりに起動します。  
  
- 各後続の試行の最初のインスタンスの実行中にアプリケーションを起動は、非常に異なる動作になります。 後続の試行では、コマンドラインの引数の詳細については、最初のインスタンスに通知し、すぐに終了します。 最初のインスタンス ハンドル、`StartupNextInstance`イベントに、後続のインスタンスのコマンドライン引数を通知し、実行が継続されます。  
  
     この図は、後続のインスタンスが最初のインスタンスを通知する方法を示しています。  
  
     ![アプリケーションのイメージを 1 つのインスタンスを示す図。](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 処理することによって、`StartupNextInstance`イベント、単一インスタンス アプリケーションの動作を制御できます。 たとえば、Microsoft Outlook は、通常; 単一インスタンス アプリケーションとして実行します。Outlook が実行されていると、Outlook を起動しようとしたときにも、元のインスタンスにフォーカスを移動が、別のインスタンスは開くことができません。  
  
## <a name="events-in-the-application-model"></a>アプリケーション モデル内のイベント  
 アプリケーション モデルでは、次のイベントにあります。  
  
- **アプリケーションの起動**します。 アプリケーションが、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>イベントの開始時にします。 このイベントを処理することによって、メイン フォームが読み込まれる前に、アプリケーションを初期化するコードを追加できます。 `Startup`必要な場合、このイベントも、起動プロセスのフェーズでは、そのアプリケーションの実行の取り消しの提供します。  
  
     アプリケーションのスタートアップ コードが実行中に、スプラッシュ スクリーンを表示するアプリケーションを構成することができます。 既定では、アプリケーション モデルは、ロゴを抑制するときに画面か、`/nosplash`または`-nosplash`コマンドライン引数を使用します。  
  
- **単一インスタンス アプリケーション**します。 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>単一インスタンスのアプリケーションの後続のインスタンスの起動時にイベントが発生します。 イベントは、後続のインスタンスのコマンドライン引数を渡します。  
  
- **未処理の例外**します。 アプリケーションには、ハンドルされない例外が発生すると、生成、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>イベント。 そのイベントのハンドラーは、例外を確認し、実行を続行するかどうかを判断できます。  
  
     `UnhandledException`イベントは、いくつかの状況では発生しません。 詳細については、「 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> 」を参照してください。  
  
- **ネットワーク接続の変更**します。 アプリケーションが発生しているコンピューターのネットワークの可用性が変更された場合、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>イベント。  
  
     `NetworkAvailabilityChanged`イベントは、いくつかの状況では発生しません。 詳細については、「 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> 」を参照してください。  
  
- **アプリケーションのシャット ダウン**します。 アプリケーションでは、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>をシャット ダウンするときに通知するイベントです。 イベントのハンドラーを行うことができますを実行する必要が、アプリケーションを操作することを確認して — を閉じると、保存、たとえば: が完了します。 アプリケーションをメイン フォームが閉じたときにシャット ダウンするか、すべてのフォームを閉じるときのみをシャット ダウンを構成することができます。  
  
## <a name="availability"></a>可用性  
 既定では、Visual Basic アプリケーション モデルは Windows フォーム プロジェクトで使用できます。 異なるスタートアップ オブジェクトを使用するアプリケーションを構成またはカスタム アプリケーション コードを開始するかどうか`Sub Main`、し、そのオブジェクトまたはクラスは、の実装を提供する必要があります、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>アプリケーション モデルを使用するクラス。 スタートアップ オブジェクトを変更する方法の詳細については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Visual Basic アプリケーション モデルの拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
