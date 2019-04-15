---
title: '方法: Windows フォームの MonthCalendar コントロールの外観を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 233143099996759cc006b3f28b984938554a0d18
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199922"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>方法: Windows フォームの MonthCalendar コントロールの外観を変更する
Windows フォーム<xref:System.Windows.Forms.MonthCalendar>コントロールでは、さまざまな方法で、カレンダーの外観をカスタマイズできます。 たとえば、配色を設定でき、または週数と現在の日付を非表示に選択できます。  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>月間予定表の配色を変更するには  
  
-   プロパティを設定します。 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>、<xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>と<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>します。 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>も、プロパティは、曜日のフォントの色を決定します。 <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>プロパティ直前および直後の表示されている月または数か月の日付の色を決定します。  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    >  以降 Windows vista では、テーマによっては、いくつかのプロパティを設定する可能性がありますいないの外観を変更、予定表。 Windows が設定されて、Aero のテーマを使用する場合の設定など、 <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>、 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>、 <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>、または<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>プロパティは影響を与えません。 これは、実行時に、現在のオペレーティング システム テーマから派生した外観の予定表の更新バージョンがレンダリングされるためです。 これらのプロパティを使用し、カレンダーの以前のバージョンを有効にする場合は、アプリケーションの visual スタイルが無効にできます。 Visual スタイルを無効にすると、アプリケーションでは、その他のコントロールの動作と外観が影響可能性があります。 Visual Basic での visual スタイルを無効にするには、プロジェクト デザイナーを開きし、オフに、**を有効にする XP visual スタイル**チェック ボックスをオンします。 C# での visual スタイルを無効にする Program.cs を開きをコメント アウト`Application.EnableVisualStyles();`します。 Visual スタイルの詳細については、次を参照してください。 [Visual スタイルを有効にする](/windows/desktop/controls/cookbook-overview)します。  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>コントロールの下部にある現在の日付を表示するには  
  
-   <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> プロパティを `true`に設定します。 次の例は、フォームがダブルクリックされたときに、今日の日付を省略すると表示を切り替えます。  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     (Visual c#、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターで、次のコードを配置します。  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>週番号を表示するには  
  
-   <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> プロパティを `true`に設定します。 コードで、または [プロパティ] ウィンドウで、このプロパティを設定できます。  
  
     別の列の週の最初の日の左側に週番号が表示されます。  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>関連項目

- [MonthCalendar コントロール](monthcalendar-control-windows-forms.md)
- [方法: Windows フォームの MonthCalendar コントロールで日付の範囲を選択する](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [方法: Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [方法: Windows フォームの MonthCalendar コントロールで複数の月を表示する](display-more-than-one-month-wf-monthcalendar-control.md)
