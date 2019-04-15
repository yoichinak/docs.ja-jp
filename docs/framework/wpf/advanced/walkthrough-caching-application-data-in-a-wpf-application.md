---
title: 'チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: 1d00c222dabf446c7c102307c3b904d3f1ff4bca
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314396"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ
キャッシュを使用すると、メモリにデータを格納して高速にアクセスできます。 アプリケーションからそのデータに再アクセスするときに、元のソースからではなく、キャッシュからデータを取得できます。 そのため、パフォーマンスとスケーラビリティが向上します。 また、データ ソースが一時的に使用できない場合でも、キャッシュのデータを使用できます。

 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]でキャッシュを使用するためのクラスを提供します[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アプリケーション。 これらのクラスにある、<xref:System.Runtime.Caching>名前空間。

> [!NOTE]
>  <xref:System.Runtime.Caching>名前空間はの新機能、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]します。 この名前空間は、すべてに使用可能なキャッシュは[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アプリケーション。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の以前のバージョンでは、キャッシュは <xref:System.Web> 名前空間でのみ使用可能だったため、ASP.NET クラスへの依存が必要でした。

 このチュートリアルで使用できるキャッシュ機能を使用する方法、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]の一部として、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーション。 チュートリアルでは、テキスト ファイルの内容をキャッシュします。

 このチュートリアルでは、以下のタスクを行います。

-   WPF アプリケーション プロジェクトを作成します。

-   参照を追加、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]します。

-   キャッシュを初期化しています。

-   テキスト ファイルの内容を格納するキャッシュ エントリを追加します。

-   キャッシュ エントリの削除ポリシーを提供します。

-   キャッシュされたファイルのパスの監視と通知する、キャッシュ インスタンスは、監視対象の項目に変更します。

## <a name="prerequisites"></a>必須コンポーネント
 このチュートリアルを完了するための要件は次のとおりです。

-   Microsoft Visual Studio 2010。

-   少量のテキストを含むテキスト ファイル。 (テキスト ファイルの内容は、メッセージ ボックスに表示されます)。このチュートリアルで示すコードでは、次のファイルを使用していることを前提としています。

     `c:\cache\cacheText.txt`

     ただし、テキスト ファイルを使用し、このチュートリアルのコードに小さな変更を加えることができます。

## <a name="creating-a-wpf-application-project"></a>WPF アプリケーション プロジェクトを作成します。
 WPF アプリケーション プロジェクトの作成から始めます。

#### <a name="to-create-a-wpf-application"></a>WPF アプリケーションを作成するには

1. Visual Studio を起動します。

2. **ファイル** メニューのをクリックして**新規**、 をクリックし、**新しいプロジェクト**します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3. **インストールされたテンプレート**、使用するプログラミング言語を選択します (**Visual Basic**または**Visual c#**)。

4. **新しいプロジェクト**ダイアログ ボックスで、 **WPF アプリケーション**します。

    > [!NOTE]
    >  表示されない場合、 **WPF アプリケーション**テンプレートのバージョンをターゲットにするかどうかを確認、 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] WPF をサポートします。 **新しいプロジェクト**ダイアログ ボックスで、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]一覧から。

5. **名前**テキスト ボックスに、プロジェクトの名前を入力します。 たとえば、入力**WPFCaching**します。

6. **[ソリューションのディレクトリを作成]** チェック ボックスをオンにします。

7. **[OK]** をクリックします。

     WPF デザイナーで開きます**デザイン**を表示し、MainWindow.xaml ファイルを表示します。 Visual Studio によって作成、 **My Project**フォルダーや、Application.xaml ファイル MainWindow.xaml ファイル。

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>.NET Framework を対象として、キャッシュのアセンブリへの参照を追加します。
 既定では、WPF アプリケーションのターゲットによって、[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]します。 使用する、 <xref:System.Runtime.Caching> WPF アプリケーションで名前空間は、アプリケーションを対象にする、 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (いない、 [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) 名前空間への参照を含める必要があります。

 したがって、次の手順が、.NET Framework のターゲットを変更しへの参照を追加するは、<xref:System.Runtime.Caching>名前空間。

> [!NOTE]
>  .NET Framework のターゲットを変更する手順は、Visual Basic プロジェクトおよび Visual c# プロジェクトでは異なります。

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Visual Basic での .NET Framework のターゲットを変更するには

1. **ソリューション エクスプ ローラー**プロジェクト名を右クリックし、クリックして**プロパティ**します。

     アプリケーションのプロパティ ウィンドウが表示されます。

2. **[コンパイル]** タブをクリックします。

3. ウィンドウの下部には、をクリックして**詳細コンパイル オプション**.

     **コンパイラの詳細設定** ダイアログ ボックスが表示されます。

4. **ターゲット フレームワーク (すべての構成)** 一覧で、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]します。 (選択しないでください[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)])。

5. **[OK]** をクリックします。

     **[ターゲット フレームワークの変更]** ダイアログ ボックスが表示されます。

6. **ターゲット フレームワークの変更**ダイアログ ボックスで、をクリックして**はい**します。

     プロジェクトは閉じられ、再度は。

7. 次の手順では、キャッシュのアセンブリへの参照を追加します。

    1.  **ソリューション エクスプ ローラー**プロジェクトの名前を右クリックし、クリックして**参照の追加**します。

    2.  選択、 **.NET** ] タブで [ `System.Runtime.Caching`、順にクリックします**OK**します。

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Visual c# プロジェクトで .NET Framework ターゲットを変更するには

1. **ソリューション エクスプ ローラー**プロジェクト名を右クリックし、クリックして**プロパティ**します。

     アプリケーションのプロパティ ウィンドウが表示されます。

2. **[アプリケーション]** タブをクリックします。

3. **ターゲット フレームワーク**一覧で、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]します。 (選択しないでください **.NET Framework 4 Client Profile**)。

4. 次の手順では、キャッシュのアセンブリへの参照を追加します。

    1.  右クリックし、**参照**フォルダーをクリック**参照の追加**します。

    2.  選択、 **.NET** ] タブで [ `System.Runtime.Caching`、順にクリックします**OK**します。

## <a name="adding-a-button-to-the-wpf-window"></a>WPF ウィンドウにボタンの追加
 次に、ボタン コントロールを追加し、ボタンのイベント ハンドラーを作成`Click`イベント。 後で、テキスト ファイルの内容がキャッシュされ、表示されるボタンをクリックすると、コードを追加します。

#### <a name="to-add-a-button-control"></a>ボタン コントロールを追加するには

1. **ソリューション エクスプ ローラー**、開く MainWindow.xaml ファイルをダブルクリックします。

2. **ツールボックス** **コモン WPF コントロール** 、ドラッグ、 `Button` への制御、 `MainWindow` ウィンドウ。

3. **プロパティ**ウィンドウで、設定、`Content`のプロパティ、`Button`に制御を**取得キャッシュ**します。

## <a name="initializing-the-cache-and-caching-an-entry"></a>キャッシュの初期化とエントリをキャッシュ
 次に、次のタスクを実行するコードを追加します。

-   キャッシュ クラスのインスタンスを作成-これは、インスタンス化する新しい<xref:System.Runtime.Caching.MemoryCache>オブジェクト。

-   キャッシュが使用するように指定、<xref:System.Runtime.Caching.HostFileChangeMonitor>のテキスト ファイルの変更を監視するオブジェクト。

-   テキスト ファイルを読み取るし、キャッシュ エントリとしてその内容をキャッシュします。

-   キャッシュされたテキスト ファイルの内容を表示します。

#### <a name="to-create-the-cache-object"></a>キャッシュ オブジェクトを作成するには

1. MainWindow.xaml.cs または MainWindow.Xaml.vb ファイルで、イベント ハンドラーを作成するために追加したボタンをダブルクリックします。

2. 次のコードを追加 (クラス宣言) の前に、ファイルの上部にある`Imports`(Visual Basic) または`using`ステートメント (c#)。

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. イベント ハンドラーでは、キャッシュ オブジェクトをインスタンス化する次のコードを追加します。

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <xref:System.Runtime.Caching.ObjectCache>クラスは、メモリ内オブジェクト キャッシュを提供する組み込みのクラスです。

4. という名前のキャッシュ エントリの内容を読み取るには、次のコードを追加`filecontents`:

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. キャッシュ エントリが名前付きかどうかを確認するには、次のコードを追加`filecontents`存在します。

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     指定したキャッシュ エントリが存在しない場合は、テキスト ファイルの読み取りし、キャッシュのエントリとしてキャッシュに追加する必要があります。

6. `if/then`ブロック、新たに作成する次のコードを追加<xref:System.Runtime.Caching.CacheItemPolicy>キャッシュ エントリが 10 秒後に有効期限が切れるを指定するオブジェクト。

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     削除または有効期限の情報が指定されていない場合、既定値は<xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>、絶対時間にのみに基づいて切れないので、キャッシュ エントリ。 代わりに、キャッシュ エントリは、メモリ負荷がある場合にのみ有効期限します。 ベスト プラクティスとして、絶対またはスライド式有効期限のいずれかを常に明示的に指定する必要があります。

7. 内で、`if/then`をブロックし、前の手順で追加したコードの後を監視して、コレクションにテキスト ファイルのパスを追加するファイルのパスのコレクションを作成するには、次のコードを追加します。

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    >  使用するテキスト ファイルがない`c:\cache\cacheText.txt`、テキスト ファイルが使用する場所のパスを指定します。

8. 新しいを追加するには、次のコードを追加する前の手順で追加したコードを次<xref:System.Runtime.Caching.HostFileChangeMonitor>キャッシュ エントリの変更のコレクションにオブジェクトを監視します。

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <xref:System.Runtime.Caching.HostFileChangeMonitor>オブジェクトは、テキスト ファイルのパスを監視し、変更が発生した場合、キャッシュに通知します。 この例で、ファイルの内容が変更された場合、キャッシュ エントリの有効期限します。

9. 前の手順で追加したコードの後に、テキスト ファイルの内容を読み取るには、次のコードを追加します。

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     キャッシュ エントリの有効期限が切れるときに表示できるように、日付と時刻のタイムスタンプが追加されます。

10. としてキャッシュ オブジェクトに、ファイルの内容を挿入する次のコードを追加する前の手順で追加したコードの後、<xref:System.Runtime.Caching.CacheItem>インスタンス。

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     渡すことによって、キャッシュ エントリを削除する方法に関する情報を指定する、<xref:System.Runtime.Caching.CacheItemPolicy>をパラメーターとして、先ほど作成したオブジェクト。

11. 後に、`if/then`ブロック、メッセージ ボックスに、キャッシュされたファイルの内容を表示する次のコードを追加します。

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. **ビルド** メニューのをクリックして**ビルド WPFCaching**プロジェクトをビルドします。

## <a name="testing-caching-in-the-wpf-application"></a>WPF アプリケーションでのキャッシュのテスト
 アプリケーションをテストすることができます。

#### <a name="to-test-caching-in-the-wpf-application"></a>WPF アプリケーションでキャッシュをテストするには

1. Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。

     `MainWindow`ウィンドウが表示されます。

2. クリックして**キャッシュを取得する**します。

     テキスト ファイルからキャッシュされたコンテンツは、メッセージ ボックスに表示されます。 ファイルのタイムスタンプに注目してください。

3. メッセージ ボックスを閉じ、クリックして**取得キャッシュ**もう一度です。

     タイムスタンプは変更されません。 これは、キャッシュされたコンテンツの表示を示します。

4. クリックして、10 秒以上待機**取得キャッシュ**もう一度です。

     この時間に、新しいタイムスタンプが表示されます。 これは、ポリシーが有効期限が切れるキャッシュ エントリを使用し、新しいキャッシュされたコンテンツが表示されることを示します。

5. テキスト エディターで作成したテキスト ファイルを開きます。 すべての変更をまだしないでください。

6. メッセージ ボックスを閉じ、クリックして**取得キャッシュ**もう一度です。

     もう一度、タイムスタンプに注目してください。

7. テキスト ファイルに変更を加えるし、ファイルを保存します。

8. メッセージ ボックスを閉じ、クリックして**取得キャッシュ**もう一度です。

     このメッセージ ボックスには、テキスト ファイルと新しいタイムスタンプから更新されたコンテンツが含まれています。 これは、ホスト ファイルの変更モニター削除されるキャッシュ エントリ、ファイルを変更したときにすぐに、絶対のタイムアウト期間の有効期限が切れていない場合でもを示します。

    > [!NOTE]
    >  ファイルを変更するための時間を 20 秒以上削除時間を増やすことができます。

## <a name="code-example"></a>コード例
 このチュートリアルを完了すると後に、作成したプロジェクトのコードが次の例のようになります。

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [.NET Framework アプリケーションでのキャッシュ](../../performance/caching-in-net-framework-applications.md)
