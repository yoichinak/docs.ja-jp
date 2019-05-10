---
title: Visual Basic アプリケーション モデルの拡張
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: bb87879fdf584a439e09839bf4321b85e7dd6a43
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602446"
---
# <a name="extending-the-visual-basic-application-model"></a>Visual Basic アプリケーション モデルの拡張
アプリケーション モデルに機能を追加するにはオーバーライドすることで、`Overridable`のメンバー、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>クラス。 この手法を使用すると、アプリケーション モデルの動作をカスタマイズし、アプリケーションの起動およびシャット ダウン、独自のメソッドの呼び出しを追加できます。  
  
## <a name="visual-overview-of-the-application-model"></a>アプリケーション モデルの視覚的な概要  
 ここでは、視覚的に、Visual Basic アプリケーション モデルで関数呼び出しのシーケンスを示します。 次のセクションでは、詳細の各関数の目的について説明します。  
  
 次の図は、通常 Visual Basic Windows フォーム アプリケーションでのアプリケーション モデルの呼び出しシーケンスを示します。 ときに、シーケンスの開始、`Sub Main`プロシージャの呼び出し、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>メソッド。  
  
 ![アプリケーション モデルの呼び出しシーケンスを示す図。](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)  
  
 Visual Basic アプリケーション モデルを使用することも、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>と<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>イベント。 次の図は、これらのイベントを発生させるためのメカニズムを示します。  
  
 ![インスタンスのイベントを発生させる OnStartupNextInstance メソッドを示す図。](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)  
  
 ![UnhandledException イベントを発生させる OnUnhandledException メソッドを示す図。](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)  
  
## <a name="overriding-the-base-methods"></a>基本メソッドのオーバーライド  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>メソッドでは、順序を定義する、`Application`メソッドを実行します。 既定で、 `Sub Main` Windows フォーム アプリケーションのプロシージャを呼び出す、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>メソッド。  
  
 アプリケーションが通常のアプリケーション (複数インスタンスのアプリケーション)、または単一インスタンスのアプリケーションの最初のインスタンスの場合、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>メソッドが実行される、`Overridable`方法を次の順序で。  
  
1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Visual スタイル、テキスト表示スタイル、および現在のプリンシパル (アプリケーションでは、Windows 認証を使用) する場合は、メイン アプリケーション スレッドの既定では、このメソッドを設定し、呼び出し`ShowSplashScreen`どちらの場合`/nosplash`も`-nosplash`として提供される、コマンドライン引数。  
  
     この関数が返す場合、アプリケーションの起動処理が取り消された`False`します。 アプリケーションを実行しない状況がある場合に役立ちます。 ことができます。  
  
     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>メソッドは、次のメソッドを呼び出します。  
  
    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. アプリケーションのスプラッシュ スクリーンが定義されているかどうかを判断し、場合は、別のスレッドでスプラッシュ スクリーンを表示します。  
  
         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>メソッドには、スプラッシュを表示するコードが含まれています。 少なくともによって指定されたミリ秒数での画面、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>プロパティ。 この機能を使用するを使用して、アプリケーションにスプラッシュ スクリーンを追加する必要があります、**プロジェクト デザイナー** (どのセット、`My.Application.MinimumSplashScreenDisplayTime`プロパティを 2 秒)、設定や、 `My.Application.MinimumSplashScreenDisplayTime` をオーバーライドするメソッドのプロパティ<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>または<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>メソッド。 詳細については、「 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> 」を参照してください。  
  
    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. によって、デザイナーのスプラッシュ スクリーンを初期化するコードを生成できます。  
  
         既定では、このメソッドは何もしません。 Visual Basic でのアプリケーションのスプラッシュ スクリーンを選択するかどうかは**プロジェクト デザイナー**、デザイナーをオーバーライドし、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>メソッドを設定するメソッド、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>プロパティ スプラッシュ スクリーンのフォームの新しいインスタンスを.  
  
2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. 発生させるための機能拡張ポイントを提供します、`Startup`イベント。 この関数が返す場合、アプリケーションの起動処理が停止します`False`します。  
  
     既定では、このメソッドは<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>イベント。 イベント ハンドラーが設定されている場合、<xref:System.ComponentModel.CancelEventArgs.Cancel>にイベント引数の`True`、メソッドを返します`False`をアプリケーションの起動を取り消します。  
  
3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. メインのアプリケーションが、初期化が完了したら、実行を開始する準備ができてときの開始点を提供します。  
  
     既定が、Windows フォームのメッセージ ループに入る前にこのメソッドは、 `OnCreateMainForm` (アプリケーションのメイン フォームを作成) して`HideSplashScreen`(スプラッシュ スクリーンを閉じる) をメソッド。  
  
    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. デザイナーがメイン フォームを初期化するコードを生成するための方法を提供します。  
  
         既定では、このメソッドは何もしません。 ただし、Visual Basic でのアプリケーションのメイン フォームを選択すると**プロジェクト デザイナー**、デザイナーをオーバーライドし、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>メソッドを設定するメソッドを使用して、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>プロパティをメイン フォームの新しいインスタンス。  
  
    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. アプリケーションがスプラッシュ スクリーンが定義されている、開いている場合は、このメソッドは、スプラッシュ スクリーンを閉じます。  
  
         既定では、このメソッドは、スプラッシュ スクリーンを閉じます。  
  
4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. アプリケーションの別のインスタンスの起動時の単一インスタンスのアプリケーションの動作をカスタマイズする方法を提供します。  
  
     既定では、このメソッドは<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>イベント。  
  
5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. 発生させるための機能拡張ポイントを提供します、`Shutdown`イベント。 このメソッドは、メイン アプリケーションでハンドルされない例外が発生した場合に実行されません。  
  
     既定では、このメソッドは<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>イベント。  
  
6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. 上記の一覧表示されているメソッドのいずれかでハンドルされない例外が発生した場合に実行されます。  
  
     既定では、このメソッド、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>イベントは、デバッガーがアタッチされていないと、アプリケーションの処理とならない限り、`UnhandledException`イベント。  
  
 アプリケーションの後続のインスタンスを呼び出すアプリケーションが単一インスタンス アプリケーションでは、アプリケーションが既に実行中の場合、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>アプリケーション、および 終了の元のインスタンス上のメソッド。  
 
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)>コンス トラクターの呼び出し、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>アプリケーションのフォームを使用するどのテキスト レンダリング エンジンを決定するプロパティ。 既定で、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>プロパティが返す`False`、これには、既定で GDI のテキスト レンダリング エンジンを使用することを示す、[!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]します。 オーバーライドすることができます、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>プロパティを返す`True`GDI + テキスト レンダリング エンジンを使用することを示します Visual Basic .NET 2002 および Visual Basic .NET 2003 の既定値します。  
  
## <a name="configuring-the-application"></a>アプリケーションを構成します。  
 Visual Basic アプリケーション モデルの一部として、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering>クラスには、アプリケーションを構成する保護対象のプロパティが用意されています。 これらのプロパティは、実装するクラスのコンス トラクターで設定する必要があります。  
  
 既定の Windows フォーム プロジェクトで、**プロジェクト デザイナー**デザイナーの設定とプロパティを設定するコードを作成します。 アプリケーションの起動時にのみ、プロパティを使用します。アプリケーションの起動後に設定しても効果はありません。  
  
|プロパティ|決定します|プロジェクト デザイナーの [アプリケーション] ウィンドウで設定|  
|---|---|---|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|かどうか、アプリケーションは、単一インスタンスまたは複数のインスタンスのアプリケーションとして実行されます。|**アプリケーションの 1 つのインスタンスを作成する** チェック ボックス|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|場合は、アプリケーションでは、Windows XP に一致する visual スタイルを使用します。|**XP visual スタイルを有効にする** チェック ボックス|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|場合は、アプリケーションの終了時に、アプリケーションは自動的にアプリケーションのユーザー設定の変更を保存します。|**シャット ダウン時に My.Settings を保存する** チェック ボックス|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|アプリケーションは、スタートアップ フォームが閉じるとき、または最後のフォームが閉じたときなど、終了の原因は何です。|**シャット ダウン モード**一覧|  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Visual Basic アプリケーション モデルの概要](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
