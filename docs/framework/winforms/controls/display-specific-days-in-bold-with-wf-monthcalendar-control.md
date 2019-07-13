---
title: '方法: Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
ms.openlocfilehash: 27b19e47d108b9af43a6d8882264d62c726ffe56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972082"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>方法: Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する
Windows フォーム<xref:System.Windows.Forms.MonthCalendar>コントロールは、単数形の日付または繰り返しごとに、太字での日を表示できます。 休日や週末などの特別な日に注目させるためにこれを行う場合があります。  
  
 次の 3 つのプロパティは、この機能を制御します。 <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>プロパティには、1 つの日付が含まれています。 <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>プロパティには、毎年を太字で表示される日付が含まれています。 <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>プロパティには、毎月を太字で表示される日付が含まれています。 これらの各プロパティの配列を含む<xref:System.DateTime>オブジェクト。 を追加またはこれらのリストのいずれかから日付を削除するには、追加または削除する必要があります、<xref:System.DateTime>オブジェクト。  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>日付を太字で表示するには  
  
1. 作成、<xref:System.DateTime>オブジェクト。  
  
    ```vb  
    Dim myVacation1 As Date = New DateTime(2001, 6, 10)  
    Dim myVacation2 As Date = New DateTime(2001, 6, 17)  
    ```  
  
    ```csharp  
    DateTime myVacation1 = new DateTime(2001, 6, 10);  
    DateTime myVacation2 = new DateTime(2001, 6, 17);  
    ```  
  
    ```cpp  
    DateTime myVacation1 = DateTime(2001, 6, 10);  
    DateTime myVacation2 = DateTime(2001, 6, 17);  
    ```  
  
2. 呼び出すことによって、1 つの日付を太字、 <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>、 <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>、または<xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A>のメソッド、<xref:System.Windows.Forms.MonthCalendar>コントロール。  
  
    ```vb  
    MonthCalendar1.AddBoldedDate(myVacation1)  
    MonthCalendar1.AddBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.AddBoldedDate(myVacation1);  
    monthCalendar1.AddBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->AddBoldedDate(myVacation1);  
    monthCalendar1->AddBoldedDate(myVacation2);  
    ```  
  
     または  
  
     太字に日付のセットを一度にすべての配列を作成して<xref:System.DateTime>オブジェクトとプロパティのいずれかに割り当てます。  
  
    ```vb  
    Dim VacationDates As DateTime() = {myVacation1, myVacation2}  
    MonthCalendar1.BoldedDates = VacationDates  
    ```  
  
    ```csharp  
    DateTime[] VacationDates = {myVacation1, myVacation2};  
    monthCalendar1.BoldedDates = VacationDates;  
    ```  
  
    ```cpp  
    Array<DateTime>^ VacationDates = {myVacation1, myVacation2};  
    monthCalendar1->BoldedDates = VacationDates;  
    ```  
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>日付を通常のフォントで表示するには  
  
1. 1 つの太字で表示される日付を呼び出すことによって通常フォントで表示、 <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>、 <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>、または<xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>メソッド。  
  
    ```vb  
    MonthCalendar1.RemoveBoldedDate(myVacation1)  
    MonthCalendar1.RemoveBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveBoldedDate(myVacation1);  
    monthCalendar1.RemoveBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveBoldedDate(myVacation1);  
    monthCalendar1->RemoveBoldedDate(myVacation2);  
    ```  
  
     または  
  
     3 つのリストのいずれかから呼び出すことによって、すべての太字で表示される日付を削除、 <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>、 <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>、または<xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>メソッド。  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. 呼び出すことによって、フォントの外観を更新、<xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>メソッド。  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>関連項目

- [MonthCalendar コントロール](monthcalendar-control-windows-forms.md)
- [方法: Windows フォームの MonthCalendar コントロールで日付の範囲を選択します。](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [方法: Windows フォーム MonthCalendar コントロールの外観を変更します。](how-to-change-monthcalendar-control-appearance.md)
- [方法: Windows フォームの MonthCalendar コントロールにおいて複数の月を表示します。](display-more-than-one-month-wf-monthcalendar-control.md)
