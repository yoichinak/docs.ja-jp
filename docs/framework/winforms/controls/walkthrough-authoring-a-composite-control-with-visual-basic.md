---
title: 'チュートリアル: Visual Basic による複合コントロールの作成'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: 5eaa92b6294ebf849f005f6e12d2dacb43fa4d6c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714282"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>チュートリアル: Visual Basic による複合コントロールの作成
複合コントロールは、カスタム グラフィカル インターフェイスを作成し、再利用するための手段を提供します。 複合コントロールは、基本的には視覚的に表示されるコンポーネントです。 そのため、複合コントロールは、1 つ以上の Windows フォーム コントロール、コンポーネント、または機能を拡張できるコード ブロックで構成されます。コード ブロックでは、ユーザー入力の検証、表示プロパティの変更、作成者が必要とする他のタスクの実行などによって機能を拡張します。 複合コントロールは、他のコントロールと同様に Windows フォームに配置できます。 このチュートリアルの前半では、`ctlClock` という単純な複合コントロールを作成します。 チュートリアルの後半では、継承によって `ctlClock` の機能を拡張します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 新しいプロジェクトを作成するときは、ルート名前空間、アセンブリ名、プロジェクト名を設定し、既定のコンポーネントが適切な名前空間に含まれるようにするために、プロジェクトの名前を指定します。  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>ctlClockLib コントロール ライブラリと ctlClock コントロールを作成するには  
  
1.  **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックして **[新しいプロジェクト]** ダイアログ ボックスを開きます。  
  
2.  Visual Basic プロジェクトのリストから選択、 **Windows コントロール ライブラリ**プロジェクト テンプレート、型`ctlClockLib`で、**名前**ボックスし、順にクリックします **[ok]**。  
  
     プロジェクト名 `ctlClockLib` は、既定でルート名前空間にも割り当てられます。 ルート名前空間は、アセンブリ内のコンポーネント名の修飾に使用されます。 たとえば、`ctlClock` という名前のコンポーネントが 2 つのアセンブリに含まれている場合、`ctlClockLib.ctlClock.` を使用して目的の `ctlClock` コンポーネントを指定できます。  
  
3.  ソリューション エクスプローラーで、**[UserControl1.vb]** を右クリックし、**[名前の変更]** をクリックします。 ファイル名を `ctlClock.vb` に変更します。 コード要素 "UserControl1" へのすべての参照の名前を変更するかどうかをたずねられたら、**[はい]** をクリックします。  
  
    > [!NOTE]
    >  既定では、複合コントロールを継承から、<xref:System.Windows.Forms.UserControl>システムによって提供されるクラス。 <xref:System.Windows.Forms.UserControl>クラスは、すべての複合コントロールに必要な機能を提供し、標準的なメソッドとプロパティを実装します。  
  
4.  **[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>複合コントロールへの Windows コントロールとコンポーネントの追加  
 ビジュアル インターフェイスは、複合コントロールに不可欠な部分です。 このビジュアル インターフェイスは、デザイナー画面に 1 つ以上の Windows コントロールを追加することによって実装されます。 次の例では、複合コントロールに Windows コントロールを組み込み、機能を実装するコードを記述します。  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>複合コントロールに Label と Timer を追加するには  
  
1.  ソリューション エクスプローラーで、**[ctlClock.vb]** を右クリックし、**[デザイナーの表示]** をクリックします。  
  
2.  ツールボックスの **[コモン コントロール]** ノードを展開し、**[Label]** をダブルクリックします。  
  
     A<xref:System.Windows.Forms.Label>という名前のコントロール`Label1`デザイナー画面上にコントロールに追加されます。  
  
3.  デザイナーで **[Label1]** をクリックします。 [プロパティ] ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|変更後の値|  
    |--------------|---------------|  
    |**Name**|`lblDisplay`|  
    |**Text**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  **ツールボックス**の **[コンポーネント]** ノードを展開し、**[Timer]** をダブルクリックします。  
  
     <xref:System.Windows.Forms.Timer>コンポーネントは、実行時にビジュアル表現を持ちません。 そのため、コントロールと共にデザイナー画面に表示されるのではなく、コンポーネント デザイナー (デザイナー画面の下部にあるトレイ) に表示されます。  
  
5.  コンポーネント デザイナーで、クリックして**Timer1**、し、設定、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティを`1000`と<xref:System.Windows.Forms.Timer.Enabled%2A>プロパティを`True`。  
  
     <xref:System.Windows.Forms.Timer.Interval%2A>プロパティは使用すると、タイマー コンポーネントがタイマー刻みの頻度を制御します。 `Timer1` が時を刻むたびに、`Timer1_Tick` イベントのコードが実行されます。 このプロパティは、タイマーの刻み間隔をミリ秒単位で表します。  
  
6.  コンポーネント デザイナーで **[Timer1]** をダブルクリックして、`ctlClock` の `Timer1_Tick` イベントに移動します。  
  
7.  コードを次のコード サンプルのように変更します。 アクセス修飾子を `Private` から `Protected` に必ず変更してください。  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     このコードにより、現在の時刻が `lblDisplay` に表示されます。 `Timer1` の間隔が `1000` に設定されているため、このイベントは 1000 ミリ秒ごとに発生します。したがって、現在の時刻が 1 秒ごとに更新されます。  
  
8.  メソッドをオーバーライド可能に変更します。 詳細については、後述の「複合コントロールの継承」を参照してください。  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. **[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。  
  
## <a name="adding-properties-to-the-composite-control"></a>複合コントロールへのプロパティの追加  
 時計コントロールにカプセル化されました、<xref:System.Windows.Forms.Label>コントロールと<xref:System.Windows.Forms.Timer>コンポーネントは、それぞれに固有のプロパティの独自のセット。 時計コントロールを今後使用するユーザーは、これらのコントロールの個々のプロパティにアクセスすることはできませんが、適切なコード ブロックを記述することで、カスタム プロパティを作成して公開できます。 次の手順では、ユーザーが背景とテキストの色を変更できるようにするプロパティをコントロールに追加します。  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>複合コントロールにプロパティを追加するには  
  
1.  ソリューション エクスプローラーで、**[ctlClock.vb]** を右クリックし、**[コードの表示]** をクリックします。  
  
     コントロールのコード エディターが開きます。  
  
2.  `Public Class ctlClock` ステートメントを探します。 このステートメントの下に、次のコードを入力します。  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     これらのステートメントにより、作成するプロパティの値の格納に使用するプライベート変数が作成されます。  
  
3.  手順 2. の変数の宣言の下に次のコードを挿入します。  
  
    ```vb  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     上記のコードは、`Property` ステートメントを呼び出すことによって、このコントロールを今後使用するユーザーが、`ClockForeColor` と `ClockBackColor` の 2 つのカスタム プロパティを使用できるようにします。 `Get` ステートメントと `Set` ステートメントは、プロパティ値を格納および取得できるようにし、そのプロパティに適した機能を実装するコードを提供します。  
  
4.  **[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。  
  
## <a name="testing-the-control"></a>コントロールのテスト  
 コントロールはスタンドアロン プロジェクトではないため、コンテナー内でホストする必要があります。 **UserControl Test Container** でコントロールの実行時の動作をテストし、プロパティを実行します。 詳細については、「[方法 :UserControl の実行時の動作をテスト](how-to-test-the-run-time-behavior-of-a-usercontrol.md)します。  
  
#### <a name="to-test-your-control"></a>コントロールをテストするには  
  
1.  F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。  
  
2.  テスト コンテナーのプロパティ グリッドで、`ClockBackColor` プロパティを選択し、ドロップダウン矢印をクリックしてカラー パレットを表示します。  
  
3.  任意の色をクリックして選択します。  
  
     コントロールの背景色が選択した色に変更されます。  
  
4.  同様のイベント シーケンスを使用して、`ClockForeColor` プロパティが予想どおりに機能していることを確認します。  
  
5.  **[閉じる]** をクリックして、**UserControl Test Container** を閉じます。  
  
     このセクションとこれまでのセクションでは、コンポーネントと Windows コントロールをコードと組み合わせてパッケージ化し、複合コントロールの形でカスタム機能を提供する方法を説明しました。 また、複合コントロールのプロパティを公開し、完了後にコントロールをテストする方法も説明しました。 次のセクションでは、`ctlClock` をベースとして使用して、継承された複合コントロールを作成する方法を説明します。  
  
## <a name="inheriting-from-a-composite-control"></a>複合コントロールの継承  
 これまでのセクションでは、Windows コントロール、コンポーネント、コードを組み合わせて、再利用可能な複合コントロールを作成する方法を説明しました。 作成した複合コントロールをベースとして使用して、他のコントロールを作成できます。 基本クラスからクラスを派生するプロセスは "*継承*" と呼ばれます。 このセクションでは、`ctlAlarmClock` という複合コントロールを作成します。 このコントロールは、親コントロールである `ctlClock` から派生します。 ここでは、親のメソッドをオーバーライドし、新しいメソッドとプロパティを追加して、`ctlClock` の機能を拡張する方法を説明します。  
  
 継承されたコントロールを作成するには、まず、親から派生します。 これにより、親コントロールのプロパティ、メソッド、グラフィカル特性をすべて備えた新しいコントロールが作成されます。このコントロールをベースとして使用して、新しい機能や変更された機能を追加できます。  
  
#### <a name="to-create-the-inherited-control"></a>継承されたコントロールを作成するには  
  
1.  ソリューション エクスプローラーで、**[ctlClockLib]** を右クリックし、**[追加]** をポイントして、**[ユーザー コントロール]** をクリックします。  
  
     **[新しい項目の追加]** ダイアログ ボックスが開きます。  
  
2.  **[継承されたユーザー コントロール]** テンプレートを選択します。  
  
3.  **[名前]** ボックスに「`ctlAlarmClock.vb`」と入力し、**[追加]** をクリックします。  
  
     **[継承ピッカー]** ダイアログ ボックスが表示されます。  
  
4.  **[コンポーネント名]** の **[ctlClock]** をダブルクリックします。  
  
5.  ソリューション エクスプローラーで、現在のプロジェクトを参照します。  
  
    > [!NOTE]
    >  現在のプロジェクトに、**ctlAlarmClock.vb** というファイルが追加されています。  
  
### <a name="adding-the-alarm-properties"></a>アラームのプロパティの追加  
 複合コントロールにプロパティを追加する場合と同様に、継承されたコントロールにプロパティを追加します。 ここでは、プロパティ宣言の構文を使用して、コントロールに 2 つのプロパティを追加します。`AlarmTime` プロパティは、アラームを鳴らす日時の値を格納し、`AlarmSet` プロパティは、アラームが設定されているかどうかを示します。  
  
##### <a name="to-add-properties-to-your-composite-control"></a>複合コントロールにプロパティを追加するには  
  
1.  ソリューション エクスプローラーで、**[ctlAlarmClock]** を右クリックし、**[コードの表示]** をクリックします。  
  
2.  ctlAlarmClock コントロールのクラスの宣言を探します。これは、`Public Class ctlAlarmClock` と表示されています。  クラスの宣言に次のコードを挿入します。  
  
    ```vb  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>コントロールのグラフィカル インターフェイスへの追加  
 継承されたコントロールには、継承元のコントロールと同じビジュアル インターフェイスがあります。 継承されたコントロールは親コントロールと同じ内在コントロールを持ちますが、内在コントロールのプロパティは、明確に公開されていない限り使用できません。 複合コントロールに追加する場合と同様に、継承された複合コントロールのグラフィカル インターフェイスに追加できます。 引き続き、アラーム時計のビジュアル インターフェイスに、アラームが鳴っているときに点滅するラベル コントロールを追加します。  
  
##### <a name="to-add-the-label-control"></a>ラベル コントロールを追加するには  
  
1.  ソリューション エクスプローラーで、**[ctlAlarmClock]** を右クリックし、**[デザイナーの表示]** をクリックします。  
  
     メイン ウィンドウに、`ctlAlarmClock` のデザイナーが表示されます。  
  
2.  `lblDisplay` (コントロールの表示部分) をクリックし、[プロパティ] ウィンドウを表示します。  
  
    > [!NOTE]
    >  すべてのプロパティが表示されていますが、淡色表示になっています。 これは、これらのプロパティが `lblDisplay` に対してネイティブであり、[プロパティ] ウィンドウで変更したりアクセスしたりすることはできないことを示しています。 既定では、複合コントロールに含まれているコントロールは `Private` であり、どのような方法でもプロパティにはアクセスできません。  
  
    > [!NOTE]
    >  複合コントロールを今後使用するユーザーが、その内部のコントロールにアクセスできるようにする場合は、内部のコントロールを `Public` または `Protected` として宣言します。 これにより、適切なコードを使用して、複合コントロールに含まれているコントロールのプロパティの設定や変更が可能になります。  
  
3.  追加、<xref:System.Windows.Forms.Label>複合コントロールにコントロール。  
  
4.  ドラッグして、マウスを使用して、<xref:System.Windows.Forms.Label>表示ボックスのすぐ下にあるコントロール。 [プロパティ] ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|設定|  
    |--------------|-------------|  
    |**Name**|`lblAlarm`|  
    |**Text**|**Alarm!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Visible**|`False`|  
  
### <a name="adding-the-alarm-functionality"></a>アラーム機能の追加  
 前の手順では、複合コントロールでアラーム機能を有効にするためのプロパティとコントロールを追加しました。 この手順では、現在の時刻をアラームの時刻と比較して、2 つの時刻が同じである場合にアラームを鳴らして点滅させるコードを追加します。 `ctlClock` の `Timer1_Tick` メソッドをオーバーライドし、コードを追加することで、`ctlClock` の固有の機能をすべて保持しながら、`ctlAlarmClock` の機能を拡張します。  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>ctlClock の Timer1_Tick メソッドをオーバーライドするには  
  
1.  ソリューション エクスプローラーで、**[ctlAlarmClock.vb]** を右クリックし、**[コードの表示]** をクリックします。  
  
2.  `Private blnAlarmSet As Boolean` ステートメントを探します。 このステートメントのすぐ下に、次のステートメントを追加します。  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  ページの下部にある `End Class` ステートメントを探します。 `End Class` ステートメントの直前に、次のコードを追加します。  
  
    ```vb  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     このコードを追加すると、いくつかのタスクが実行されます。 `Overrides` ステートメントは、基本コントロールから継承されたメソッドの代わりに、このメソッドを使用するようコントロールに指示します。 このメソッドが呼び出されると、メソッドは `MyBase.Timer1_Tick` ステートメントを呼び出して、オーバーライドしたメソッドを呼び出します。これにより、元のコントロールに組み込まれたすべての機能がこのコントロールに継承されます。 その後、メソッドは追加のコードを実行してアラーム機能を組み込みます。 アラームが発生すると、点滅するラベル コントロールが表示され、ビープ音が聞こえます。  
  
    > [!NOTE]
    >  継承されたイベント ハンドラーをオーバーライドしているので、`Handles` キーワードでイベントを指定する必要はありません。 イベントは既にフックされています。 オーバーライドしているのはハンドラーの実装です。  
  
     これで、アラーム時計コントロールはほぼ完成です。 あとはアラームを止める方法を実装するだけです。 これを行うには、`lblAlarm_Click` メソッドにコードを追加します。  
  
##### <a name="to-implement-the-shutoff-method"></a>停止メソッドを実装するには  
  
1.  ソリューション エクスプローラーで、**[ctlAlarmClock.vb]** を右クリックし、**[デザイナーの表示]** をクリックします。  
  
2.  デザイナーで **[lblAlarm]** をダブルクリックします。 **コード エディター**が開き、`Private Sub lblAlarm_Click` 行が表示されます。  
  
3.  このメソッドを次のコードのように変更します。  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  **[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。  
  
### <a name="using-the-inherited-control-on-a-form"></a>フォームでの継承されたコントロールの使用  
 継承されたコントロールは基本クラスのコントロールをテストするのと同じ方法でテストできます`ctlClock`:F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。 詳細については、「[方法 :UserControl の実行時の動作をテスト](how-to-test-the-run-time-behavior-of-a-usercontrol.md)します。  
  
 コントロールを使用するには、フォーム上でコントロールをホストする必要があります。 標準の複合コントロールと同様に、継承された複合コントロールをスタンドアロンにすることはできないので、フォームまたは他のコンテナー内でホストする必要があります。 `ctlAlarmClock` は機能が拡張されているため、テストするには追加のコードが必要となります。 次の手順では、`ctlAlarmClock` の機能をテストするための簡単なプログラムを作成します。 `ctlAlarmClock` の `AlarmTime` プロパティを設定して表示するコードを記述し、固有の機能をテストします。  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>コントロールをビルドしてテスト フォームに追加するには  
  
1.  ソリューション エクスプローラーで、**[ctlClockLib]** を右クリックし、**[ビルド]** をクリックします。  
  
2.  **[ファイル]** メニューの **[追加]** をポイントし、 **[新しいプロジェクト]** をクリックします。  
  
3.  新しい **Windows アプリケーション** プロジェクトをソリューションに追加し、`Test` という名前を付けます。  
  
     ソリューション エクスプローラーに **Test** プロジェクトが追加されます。  
  
4.  ソリューション エクスプローラーで、`Test` プロジェクト ノードを右クリックし、**[参照の追加]** をクリックして **[参照の追加]** ダイアログ ボックスを表示します。  
  
5.  **[プロジェクト]** というラベルのタブをクリックします。 **[プロジェクト名]** に **ctlClockLib** プロジェクトが表示されます。 **[ctlClockLib]** をダブルクリックして、テスト プロジェクトへの参照を追加します。  
  
6.  ソリューション エクスプローラーで、**[Test]** を右クリックし、**[ビルド]** をクリックします。  
  
7.  **ツールボックス**で、**[ctlClockLib コンポーネント]** ノードを展開します。  
  
8.  **[ctlAlarmClock]** をダブルクリックして、`ctlAlarmClock` のインスタンスをフォームに追加します。  
  
9. **ツールボックス**をダブルクリック**DateTimePicker**を追加する、<xref:System.Windows.Forms.DateTimePicker>をフォームに制御し、追加、<xref:System.Windows.Forms.Label>コントロールをダブルクリックして**ラベル**.  
  
10. マウスを使用して、各コントロールをフォーム上の使いやすい場所に配置します。  
  
11. これらのコントロールのプロパティを次のように設定します。  
  
    |コントロール|プロパティ|[値]|  
    |-------------|--------------|-----------|  
    |`label1`|**Text**|`(blank space)`|  
    ||**Name**|`lblTest`|  
    |`dateTimePicker1`|**Name**|`dtpTest`|  
    ||**Format**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. デザイナーで **[dtpTest]** をダブルクリックします。  
  
     **コード エディター**が開き、`Private Sub dtpTest_ValueChanged` が表示されます。  
  
13. コードを次のように変更します。  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. ソリューション エクスプローラーで、**[Test]** を右クリックし、**[スタートアップ プロジェクトに設定]** をクリックします。  
  
15. **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
     テスト プログラムが起動します。 現在の時刻が更新されることに注意してください、`ctlAlarmClock`制御、およびその開始時刻を示します、<xref:System.Windows.Forms.DateTimePicker>コントロール。  
  
16. をクリックして、<xref:System.Windows.Forms.DateTimePicker>の分が表示されます。  
  
17. キーボードを使用して、`ctlAlarmClock` に表示されている現在の時刻の 1 分後の値を設定します。  
  
     アラーム設定の時刻が `lblTest` に表示されます。 表示時刻がアラーム設定時刻になるまで待ちます。 表示時刻がアラーム設定時刻になると、ビープ音が鳴り、`lblAlarm` が点滅します。  
  
18. `lblAlarm` をクリックしてアラームを止めます。 これでアラームをリセットできます。  
  
     このチュートリアルでは、多数の重要な概念を取り上げました。 コントロールとコンポーネントを複合コントロール コンテナーに組み込んで複合コントロールを作成する方法を説明しました。 また、コントロールにプロパティを追加する方法と、カスタム機能を実装するコードを記述する方法も説明しました。 最後のセクションでは、継承によって特定の複合コントロールの機能を拡張する方法と、ホスト メソッドをオーバーライドすることでメソッドの機能を変更する方法を説明しました。  
  
## <a name="see-also"></a>関連項目
- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
- [方法: 複合コントロールを作成](how-to-author-composite-controls.md)
- [方法: 内のコントロールを表示、ツールボックス項目 ダイアログ ボックスの選択](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
