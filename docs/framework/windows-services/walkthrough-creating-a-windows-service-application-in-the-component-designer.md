---
title: Visual Studio で Windows サービス アプリケーションを作成する
ms.date: 09/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: 52c2f64bbb71e07dcab1fd7cd42662f9ed2c8445
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/22/2019
ms.locfileid: "56665031"
---
# <a name="walkthrough-create-a-windows-service-app"></a>チュートリアル: Windows サービス アプリを作成する

この記事では、イベント ログにメッセージを書き込む単純な Windows サービス アプリを Visual Studio で作成する方法を示します。

## <a name="create-a-service"></a>サービスを作成する

最初に、プロジェクトを作成し、サービスが正しく機能するために必要な値を設定します。

1. Visual Studio のメニュー バーで、**[ファイル]** > **[新規]** > **[プロジェクト]** を選択して (または **Ctrl**+**Shift**+**N** を押して)、**[新しいプロジェクト]** ダイアログを開きます。

2. **[Windows サービス]** プロジェクト テンプレートに移動して選択します。 **[インストール済み]** **[Visual C#** または **Visual Basic]** **[Windows Desktop]** の順に展開するか、右上の検索ボックスに「**Windows サービス**」と入力します。

   ![Visual Studio の [新しいプロジェクト] ダイアログの Windows サービス アプリ テンプレート](media/new-project-dialog.png)

   > [!NOTE]
   > **[Windows サービス]** テンプレートが表示されない場合は、**.NET デスクトップ開発** ワークロードのインストールが必要である可能性があります。 **[新しいプロジェクト]** ダイアログで、左下にある **[Visual Studio インストーラーを開く]** リンクをクリックします。 **Visual Studio インストーラー**で、**[.NET デスクトップ開発]** ワークロードを選択し、**[変更]** ボタンを選択します。

3. プロジェクトに **MyNewService** という名前を付け、**[OK]** を選択します。

   プロジェクト テンプレートには、<xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> から継承される `Service1` という名前のコンポーネント クラスが含まれます。 それは、サービスを開始するコードなどの多数の基本的なサービス コードを含んでいます。

## <a name="rename-the-service"></a>サービスの名前を変更する

サービスの名前を **Service1** から **MyNewService** に変更します。

1. Service1.cs (または Service1.vb) の **[デザイン]** ビューで、**コード ビューに切り替える**ためのリンクをクリックします。 **[Service1]** を右クリックし、コンテキスト メニューから **[名前の変更]** を選択します。 「**MyNewService**」と入力し、**Enter** キーを押すか **[適用]** をクリックします。

2. **Service1.cs の [デザイン]** または **Service1.vb の [デザイン]** の **[プロパティ]** ウィンドウで、**ServiceName** の値を **MyNewService** に変更します。

3. **ソリューション エクスプローラー**で、**Service1.cs** を **MyNewService.cs** に、または **Service1.vb** を **MyNewService.vb** に変更します。

## <a name="add-features-to-the-service"></a>サービスに機能を追加する

このセクションでは、Windows サービスにカスタム イベント ログを追加します。 イベント ログは、Windows サービスとまったく関連付けられていません。 ここでは、Windows サービスに追加できるコンポーネントの種類の例として、<xref:System.Diagnostics.EventLog> コンポーネントを使用しています。

### <a name="add-custom-event-log-functionality"></a>サービスにカスタム イベント ログ機能を追加する

1. **ソリューション エクスプローラー**で、 **MyNewService.cs** または **MyNewService.vb**のコンテキスト メニューを開き、 **[デザイナーの表示]** を選択します。

2. **[ツールボックス]** の **[コンポーネント]** セクションから、 <xref:System.Diagnostics.EventLog> コンポーネントをデザイナーにドラッグします。

3. **ソリューション エクスプローラー**で、 **MyNewService.cs** または **MyNewService.vb**のコンテキスト メニューを開き、 **[コードの表示]** を選択します。

4. カスタム イベント ログを定義するコンストラクターを編集します。

   ```csharp
   public MyNewService()
   {
        InitializeComponent();

        eventLog1 = new System.Diagnostics.EventLog();
        if (!System.Diagnostics.EventLog.SourceExists("MySource"))
        {
            System.Diagnostics.EventLog.CreateEventSource(
                "MySource", "MyNewLog");
        }
        eventLog1.Source = "MySource";
        eventLog1.Log = "MyNewLog";
    }
   ```

   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

### <a name="define-what-occurs-when-the-service-starts"></a>サービスの開始時の処理を定義する

コード エディターで、プロジェクトの作成時に自動的にオーバーライドされた <xref:System.ServiceProcess.ServiceBase.OnStart%2A> を見つけます。 サービスの開始時にイベント ログに対するエントリーを記述するコード行を追加します。

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

サービス アプリケーションは長期間実行するように設計されているため、通常は、システム内の何かをポーリングまたは監視しています。 この監視は、 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドで設定します。 ただし、 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> は実際には監視を行いません。 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドは、サービスの操作が開始された後にオペレーティング システムに戻る必要があります。 永久的に続くループやブロックは実行できません。 簡単なポーリング メカニズムをセットアップするには、次のように <xref:System.Timers.Timer?displayProperty=nameWithType> コンポーネントを使用できます。<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドで、コンポーネントにパラメーターを設定してから、<xref:System.Timers.Timer.Enabled%2A> プロパティを `true` に設定します。 このタイマーによって、コード内で定期的にイベントが発生します。サービスは、イベントが発生するごとに監視を実行できます。 このためには、次のコードを使用できます。

```csharp
// Set up a timer that triggers every minute.
System.Timers.Timer timer = new System.Timers.Timer();
timer.Interval = 60000; // 60 seconds
timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);
timer.Start();
```

```vb
' Set up a timer that triggers every minute.
Dim timer As System.Timers.Timer = New System.Timers.Timer()
timer.Interval = 60000 ' 60 seconds
AddHandler timer.Elapsed, AddressOf Me.OnTimer
timer.Start()
```

メンバー変数をクラスに追加します。 それには、イベント ログに書き込まれる次のイベントの識別子が含まれます。

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

タイマー イベントを処理する新しいコードを追加します。

```csharp
public void OnTimer(object sender, System.Timers.ElapsedEventArgs args)
{
    // TODO: Insert monitoring activities here.
    eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);
}
```

```vb
Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)
    ' TODO: Insert monitoring activities here.
    eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)
    eventId = eventId + 1
End Sub
```

メイン スレッドですべての作業を実行するのではなく、バックグラウンド ワーカー スレッドを使用してタスクを実行する場合があります。 詳細については、「<xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>」を参照してください。

### <a name="define-what-occurs-when-the-service-is-stopped"></a>サービスの停止時の処理を定義する

サービスの停止時にイベント ログに対するエントリーを追加するコード行を <xref:System.ServiceProcess.ServiceBase.OnStop%2A> に追加します。

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>サービスに対して他の処理を定義する

<xref:System.ServiceProcess.ServiceBase.OnPause%2A>、<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>、および <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> の各メソッドをオーバーライドして、コンポーネントの処理をさらに定義できます。 次のコード例は、 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> メソッドをオーバーライドする方法を示しています。

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

いくつかのカスタム動作は、Windows サービスが <xref:System.Configuration.Install.Installer> クラスによりインストールされるときに発生する必要があります。 Visual Studio は、これらのインストーラーを Windows サービス専用に作成し、プロジェクトに追加できます。

## <a name="set-service-status"></a>サービスの状態を設定する

サービスは、その状態をサービス コントロール マネージャーに報告します。これによりユーザーは、サービスが正常に機能しているかどうかを確認することができます。 既定では、 <xref:System.ServiceProcess.ServiceBase> を継承するサービスは、[停止]、[一時停止]、[実行中] など、限られた状態設定のセットを報告します。 サービスの開始に若干時間がかかるときは、[保留の開始] 状態を報告すると役立つ場合があります。 [保留の開始] と [保留の停止] の状態設定は、Windows の [SetServiceStatus 関数](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)を呼び出すコードを追加することによって実装することもできます。

サービス保留の状態を実装するには:

1. <xref:System.Runtime.InteropServices?displayProperty=nameWithType> 名前空間に対する `using` ステートメントまたは `Imports` 宣言を MyNewService.cs ファイルまたは MyNewService.vb ファイルに追加します。

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. MyNewService.cs に次のコードを追加して、 `ServiceState` の値を宣言し、プラットフォーム呼び出しで使用する状態の構造を追加します。

    ```csharp
    public enum ServiceState
    {
        SERVICE_STOPPED = 0x00000001,
        SERVICE_START_PENDING = 0x00000002,
        SERVICE_STOP_PENDING = 0x00000003,
        SERVICE_RUNNING = 0x00000004,
        SERVICE_CONTINUE_PENDING = 0x00000005,
        SERVICE_PAUSE_PENDING = 0x00000006,
        SERVICE_PAUSED = 0x00000007,
    }

    [StructLayout(LayoutKind.Sequential)]
    public struct ServiceStatus
    {
        public int dwServiceType;
        public ServiceState dwCurrentState;
        public int dwControlsAccepted;
        public int dwWin32ExitCode;
        public int dwServiceSpecificExitCode;
        public int dwCheckPoint;
        public int dwWaitHint;
    };
    ```

    ```vb
    Public Enum ServiceState
        SERVICE_STOPPED = 1
        SERVICE_START_PENDING = 2
        SERVICE_STOP_PENDING = 3
        SERVICE_RUNNING = 4
        SERVICE_CONTINUE_PENDING = 5
        SERVICE_PAUSE_PENDING = 6
        SERVICE_PAUSED = 7
    End Enum

    <StructLayout(LayoutKind.Sequential)>
    Public Structure ServiceStatus
        Public dwServiceType As Long
        Public dwCurrentState As ServiceState
        Public dwControlsAccepted As Long
        Public dwWin32ExitCode As Long
        Public dwServiceSpecificExitCode As Long
        Public dwCheckPoint As Long
        Public dwWaitHint As Long
    End Structure
    ```

3. 次に、`MyNewService` クラスで、[プラットフォーム呼び出し](../interop/consuming-unmanaged-dll-functions.md)を使用して、[SetServiceStatus 関数](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)を宣言します。

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. [保留の開始] 状態を実装するには、 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドの先頭に次のコードを追加します。

    ```csharp
    // Update the service state to Start Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Start Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

5. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドの末尾に、状態を [実行中] に設定するコードを追加します。

    ```csharp
    // Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

6. (省略可能) <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドに対してこの手順を繰り返します。

> [!NOTE]
> [サービス コントロール マネージャー](/windows/desktop/Services/service-control-manager)は、[SERVICE_STATUS 構造体](/windows/desktop/api/winsvc/ns-winsvc-_service_status)の `dwWaitHint` メンバーと `dwCheckpoint` メンバーを使って、Windows サービスの開始やシャットダウンまでの待機時間を判断します。 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドが長時間実行している場合、サービスは、インクリメントした `dwCheckPoint` 値で [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) をもう一度呼び出すことによって、追加の時間を要求できます。

## <a name="add-installers-to-the-service"></a>サービスにインストーラーを追加する

Windows サービスを実行するには、まず、サービスをインストールする必要があります。これにより、サービスがサービス コントロール マネージャーに登録されます。 登録の詳細を処理するインストーラーをプロジェクトに追加できます。

1. **ソリューション エクスプローラー**で、 **MyNewService.cs** または **MyNewService.vb**のコンテキスト メニューを開き、 **[デザイナーの表示]** を選択します。

2. デザイナーの背景をクリックして、サービスの内容ではなくサービス自体を選択します。

3. デザイナー ウィンドウのコンテキスト メニューを開き (ポインティング デバイスを使用している場合は、ウィンドウ内を右クリック)、 **[インストーラーの追加]** を選択します。

   既定では、2 つのインストーラーを含むコンポーネント クラスがプロジェクトに追加されます。 このコンポーネントは **ProjectInstaller**という名前で、サービス用のインストーラーと、サービスの関連プロセス用のインストーラーを含んでいます。

4. **[ProjectInstaller]** の **[デザイン]** ビューで、 **[serviceInstaller1]** (Visual C# プロジェクトの場合) または **[ServiceInstaller1]** (Visual Basic プロジェクトの場合) を選択します。

5. **[プロパティ]** ウィンドウで、 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> プロパティが **MyNewService**に設定されていることを確認します。

6. **[説明]** プロパティに、「A sample service」などのテキストを設定します。 このテキストは [サービス] ウィンドウに表示されます。これによりユーザーは、サービスを識別したり、その用途を理解したりできます。

7. <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> プロパティに、[サービス] ウィンドウの **[名前]** 列に表示するテキストを設定します。 たとえば、「MyNewService Display Name」と入力できます。 この名前は、システムによって使用される (たとえば、 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> コマンドを使用してサービスを開始する場合) 名前である `net start` プロパティとは異なる名前にすることができます。

8. <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> プロパティを <xref:System.ServiceProcess.ServiceStartMode.Automatic>に設定します。

     ![Windows サービスのインストーラー プロパティ](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")

9. デザイナーで、 **[serviceProcessInstaller1]** (Visual C# プロジェクトの場合) または **[ServiceProcessInstaller1]** (Visual Basic プロジェクトの場合) を選択します。 <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> プロパティを <xref:System.ServiceProcess.ServiceAccount.LocalSystem>に設定します。 これにより、サービスがインストールされ、ローカル システム アカウントを使用して実行されます。

    > [!IMPORTANT]
    > <xref:System.ServiceProcess.ServiceAccount.LocalSystem> アカウントには、イベント ログへの書き込みを含む、幅広いアクセス許可が設定されています。 このアカウントは悪意のあるソフトウェアから攻撃されるリスクが高いため、使用する場合は注意が必要です。 その他のタスクについては、ローカル コンピューターで非特権ユーザーとして機能し、リモート サーバーには匿名の資格情報を渡す <xref:System.ServiceProcess.ServiceAccount.LocalService> アカウントの使用を検討してください。 この例は、 <xref:System.ServiceProcess.ServiceAccount.LocalService> アカウントを使用しようとすると失敗します。これは、イベント ログに書き込むアクセス許可が必要になるためです。

インストーラーについて詳しくは、「[方法: サービス アプリケーションにインストーラーを追加する](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)」をご覧ください。

## <a name="optional-set-startup-parameters"></a>(省略可能) スタートアップ パラメーターを設定する

Windows サービスは、他の実行可能ファイルと同じように、コマンド ライン引数 (スタートアップ パラメーター) を受け入れることができます。 スタートアップ パラメーターを処理するコードを追加すると、ユーザーは、Windows のコントロール パネルの [サービス] ウィンドウを使用して、カスタムのスタートアップ パラメーターによりサービスを開始できます。 ただし、これらのスタートアップ パラメーターは、次回のサービスの開始時には保持されません。 スタートアップ パラメーターを永続的に設定するために、次の手順で示すようにレジストリに設定することができます。

> [!NOTE]
> スタートアップ パラメーターを追加するよう決定する前に、これがサービスに情報を渡す最適な方法であるかどうかを検討してください。 スタートアップ パラメーターの使用や解析は簡単であり、ユーザーが簡単にオーバーライドできますが、ドキュメントなしでは検索や使用が困難である可能性があります。 一般的に、サービスに必要なスタートアップ パラメーターが複数ある場合は、代わりにレジストリまたは構成ファイルの使用を検討する必要があります。 すべての Windows サービスのレジストリのエントリは、**HKLM\System\CurrentControlSet\services** にあります。 サービスのキーで、 **Parameters** サブキーを使用して、サービスがアクセスできる情報を格納することができます。 その他の種類のプログラムの場合と同じ方法で、Windows サービスに対してアプリケーション構成ファイルを使用できます。 コード例については、「 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>」を参照してください。

スタートアップ パラメーターを追加するには:

1. Program.cs または MyNewService.Designer.vb の `Main` メソッドに、サービスのコンス トラクターに渡す入力パラメーターを追加します。

   ```csharp
   static void Main(string[] args)
   {
       ServiceBase[] ServicesToRun;
       ServicesToRun = new ServiceBase[]
       {
           new MyNewService(args)
       };
       ServiceBase.Run(ServicesToRun);
   }
   ```

   ```vb
   Shared Sub Main(ByVal cmdArgs() As String)
       Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
       System.ServiceProcess.ServiceBase.Run(ServicesToRun)
   End Sub
   ```

2. `MyNewService` コンストラクターを次のように変更します。

   ```csharp
   public MyNewService(string[] args)
   {
       InitializeComponent();

        string eventSourceName = "MySource";
        string logName = "MyNewLog";

        if (args.Length > 0)
        {
            eventSourceName = args[0];
        }

        if (args.Length > 1)
        {
            logName = args[1];
        }

        eventLog1 = new System.Diagnostics.EventLog();

        if (!System.Diagnostics.EventLog.SourceExists(eventSourceName))
        {
            System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName);
        }

        eventLog1.Source = eventSourceName;
        eventLog1.Log = logName;
   }
   ```

   ```vb
   Public Sub New(ByVal cmdArgs() As String)
       InitializeComponent()
       Dim eventSourceName As String = "MySource"
       Dim logName As String = "MyNewLog"
       If (cmdArgs.Count() > 0) Then
           eventSourceName = cmdArgs(0)
       End If
       If (cmdArgs.Count() > 1) Then
           logName = cmdArgs(1)
       End If
       eventLog1 = New System.Diagnostics.EventLog()
       If (Not System.Diagnostics.EventLog.SourceExists(eventSourceName)) Then
           System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   このコードでは、指定したスタートアップ パラメーターに従ってイベント ソースとログ名が設定されるか、引数を指定しなかった場合は既定値が使用されます。

3. コマンド ライン引数を指定するには、ProjectInstaller.cs または ProjectInstaller.vb の `ProjectInstaller` クラスに次のコードを追加します。

   ```csharp
   protected override void OnBeforeInstall(IDictionary savedState)
   {
       string parameter = "MySource1\" \"MyLogFile1";
       Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
       base.OnBeforeInstall(savedState);
   }
   ```

   ```vb
   Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
       Dim parameter As String = "MySource1"" ""MyLogFile1"
       Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
       MyBase.OnBeforeInstall(savedState)
   End Sub
   ```

   このコードでは、既定のパラメーター値を追加することによって、一般的に Windows サービスの実行可能ファイルへの完全パスが含まれる **ImagePath** レジストリ キーが変更されます。 サービスが正しく開始されるためには、パス (およびそれぞれ個々のパラメーター) を囲む引用符が必要です。 この Windows サービスのスタートアップ パラメーターを変更するために、ユーザーは、**ImagePath** レジストリ キーで指定されたパラメーターを変更できます。ただし、パラメーターをプログラムによって変更し、ユーザーに対してはわかりやすい方法 (たとえば、管理ユーティリティや構成ユーティリティ) で機能を示すことをお勧めします。

## <a name="build-the-service"></a>サービスをビルドする

1. **ソリューション エクスプローラー**で、プロジェクトのコンテキスト メニューを開き、 **[プロパティ]** を選択します。

   プロジェクトのプロパティ ページが表示されます。

2. **[アプリケーション]** タブで、**[スタートアップ オブジェクト]** ボックスの一覧の **[MyNewService.Program]** を選択します。

3. **ソリューション エクスプローラー**で、プロジェクトのコンテキスト メニューを開き、**[ビルド]** を選択してプロジェクトをビルドします (または **Ctrl**+**Shift**+**B**を押します)。

## <a name="install-the-service"></a>サービスをインストールする

Windows サービスを構築済みであるため、サービスをインストールできます。 Windows サービスをインストールするには、インストール先のコンピューターの管理者資格情報が必要です。

1. 管理者資格情報を使用して、**Visual Studio 用開発者コマンド プロンプト**を開きます。 マウスを使用している場合は、Windows の [スタート] メニューから **[Developer Command Prompt for VS 2017]/(VS 2017 用開発者コマンド プロンプト/)** を右クリックし、**[その他]** > **[管理者として実行]** を選択します。

2. **[開発者コマンド プロンプト]** ウィンドウで、プロジェクトの出力を含むフォルダーに移動します (既定では、プロジェクトの *\bin\Debug* サブディレクトリです)。

3. 次のコマンドを入力します。

    ```shell
    installutil.exe MyNewService.exe
    ```

    サービスが正常にインストールされると、正常に実行されたことが **installutil.exe** によって報告されます。 システムが **InstallUtil.exe** が見付けることができなかった場合は、コンピューター上に存在することを確認してください。 このツールは、.NET Framework と共に *%windir%\Microsoft.NET\Framework[64]\\[framework version]* フォルダーにインストールされます。 たとえば、32 ビット バージョンでの既定のパスは *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe* です。

    **installutil.exe** プロセスでエラーが報告された場合は、インストール ログを調べて理由を確認します。 既定で、ログはサービスの実行可能ファイルと同じフォルダーにあります。 <xref:System.ComponentModel.RunInstallerAttribute> クラスが `ProjectInstaller` クラスにない場合、属性が **true** に設定されていない場合、または `ProjectInstaller` クラスが **public** とマークされていない場合は、インストールが失敗する可能性があります。

詳細については、「[方法 :サービスをインストールおよびアンインストールする](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)」を参照してください。

## <a name="start-and-run-the-service"></a>サービスを開始して実行する

1. Windows で、**[サービス]** デスクトップ アプリを開きます。 **Windows**+**R** を押して **[ファイル名を指定して実行]** ボックスを開き、「**services.msc**」と入力して、**Enter** を押すか **[OK]** をクリックします。

     **[サービス]** 内にサービスが一覧表示されます。サービスは、サービスに対して設定した表示名でアルファベット順に表示されます。

     ![[サービス] ウィンドウの MyNewService。](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. **[サービス]** で、サービスのショートカット メニューを開き、**[開始]** を選択します。

3. サービスを停止するには、サービスのショートカット メニューを開き、**[停止]** を選択します。

4. (省略可能) コマンド ラインから `net start ServiceName` コマンドと `net stop ServiceName` コマンドを使用することで、サービスの開始と停止を実行できます。

### <a name="verify-the-event-log-output-of-your-service"></a>サービスのイベント ログ出力を確認する

1. Windows タスクバーの検索ボックスに**イベント ビューア―** というテキストの入力を開始し、検索結果から **[イベント ビューア―]** を選択することで、**イベント ビューアー**を開きます。

   > [!TIP]
   > Visual Studio でイベント ログにアクセスするには、**サーバー エクスプローラー**を開き (キーボード: **Ctrl** + **Alt** + **S**)、ローカル コンピューターの **[イベント ログ]** ノードを展開します。

2. **[イベント ビューアー]** で、**[アプリケーションとサービス ログ]** を展開します。

3. **MyNewLog** (または、省略可能な手順に従ってコマンド ライン引数を追加した場合は **MyLogFile1**) の一覧を見つけて展開します。 サービスが実行した 2 つの操作 (開始および停止) のエントリが表示されます。

     ![イベント ビューアーを使用してイベント ログの項目を表示する](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a>サービスをアンインストールする

1. 管理者資格情報を使用して、**Visual Studio 用開発者コマンド プロンプト**を開きます。

2. コマンド プロンプト ウィンドウで、プロジェクトの出力が格納されているフォルダーに移動します。

3. 次のコマンドを入力します。

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   サービスが正常にアンインストールされると、サービスが正常に削除されたことが **installutil.exe** によって報告されます。 詳細については、「[方法 :サービスをインストールおよびアンインストールする](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)」を参照してください。

## <a name="next-steps"></a>次の手順

これでサービスの作成は終わりましたが、作成した Windows サービスを他のユーザーがインストールするために使用できるスタンドアロン セットアップ プログラムを作成できます。 ClickOnce ではWindows サービスはサポートされませんが、[WiX Toolset](http://wixtoolset.org/) を使用して Windows サービス用のインストーラーを作成できます。 その他のアイデアについては、[インストーラー パッケージの作成](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)に関する記事を参照してください。

インストールしたサービスにコマンドを送信できる <xref:System.ServiceProcess.ServiceController> コンポーネントの使用法を調べることもできます。

インストーラーを使用すると、アプリケーションの実行時にイベント ログを作成する代わりに、アプリケーションのインストール時にイベント ログを作成できます。 さらに、イベント ログは、アプリケーションがアンインストールされたときにインストーラーによって削除されます。 詳細については、 <xref:System.Diagnostics.EventLogInstaller> のリファレンス ページを参照してください。

## <a name="see-also"></a>関連項目

- [Windows サービス アプリケーション](../../../docs/framework/windows-services/index.md)
- [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [方法: Windows サービス アプリケーションをデバッグする](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [サービス (Windows)](/windows/desktop/Services/services)
