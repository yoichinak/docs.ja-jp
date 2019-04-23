---
title: MonthCalendar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: 8928a78735392920d893661c70554bd35eba2886
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106237"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.MonthCalendar>コントロールがユーザーに表示し、日付情報を設定するための直感的なグラフィカル インターフェイスを表示します。 カレンダーを表示、: 曜日、強調表示されている日付の選択範囲を下にある列には、月の番号付きの日を含むグリッドです。 1 か月のキャプションのどちら側にある矢印ボタンをクリックして、別の月を選択できます。 異なり、類似<xref:System.Windows.Forms.DateTimePicker>コントロールでは、このコントロールでは、複数の日付を選択することができます。 詳細については、<xref:System.Windows.Forms.DateTimePicker>コントロールを参照してください[DateTimePicker コントロール](datetimepicker-control-windows-forms.md)します。  
  
## <a name="configuring-the-monthcalendar-control"></a>MonthCalendar コントロールを構成します。  
 <xref:System.Windows.Forms.MonthCalendar>コントロールの外観は高度に構成できます。 既定では、今日の日付が丸で囲まれて表示され、グリッドの下部にも示されます。 この機能を設定して変更することができます、<xref:System.Windows.Forms.MonthCalendar.ShowToday%2A>と<xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A>プロパティ`false`します。 設定して、予定表に週番号を追加することも、<xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A>プロパティを`true`します。 設定して、<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>プロパティ、複数の水平および垂直に表示する月を指定できます。 既定では、日曜日が週の最初の曜日として表示されますを使用して任意の日を指定することができます、<xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>プロパティ。  
  
 設定することも特定の日付に表示される、年間または月単位、1 回限りのベースで太字を追加して<xref:System.DateTime>オブジェクトを<xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>、 <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>、および<xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>プロパティ。 詳細については、「[方法 :特定の日で、Windows で太字で表示フォームの MonthCalendar コントロール](display-specific-days-in-bold-with-wf-monthcalendar-control.md)します。  
  
 キー プロパティ、<xref:System.Windows.Forms.MonthCalendar>コントロールが<xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>コントロールで選択した日付の範囲。 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>値が選択できる設定日の最大数を超えることはできません、<xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>プロパティ。 ユーザーが選択できる最初と最後の日付が定め、<xref:System.Windows.Forms.MonthCalendar.MaxDate%2A>と<xref:System.Windows.Forms.MonthCalendar.MinDate%2A>プロパティ。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MonthCalendar>
- [MonthCalendar コントロール](monthcalendar-control-windows-forms.md)
