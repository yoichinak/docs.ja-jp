---
title: '方法: Windows フォームの MonthCalendar コントロールで複数の月を表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
ms.openlocfilehash: 79100b52d8e0a5b651edb9d6555a4497287ed858
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209555"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>方法: Windows フォームの MonthCalendar コントロールで複数の月を表示する
Windows フォーム<xref:System.Windows.Forms.MonthCalendar>コントロールは、一度に最大 12 か月を表示できます。 既定では、コントロールには、1 か月が表示されますが、数か月間が表示され、コントロール内の配置方法を指定することができます。 Calendar ディメンションを変更すると、コントロールのサイズ変更、あるため、新しいディメンションのフォームに十分な空き領域があることを確認します。  
  
### <a name="to-display-multiple-months"></a>複数の月を表示するには  
  
-   設定、<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>プロパティに水平および垂直に表示する月の数。  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>関連項目

- [MonthCalendar コントロール](monthcalendar-control-windows-forms.md)
- [方法: Windows フォームの MonthCalendar コントロールで日付の範囲を選択します。](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [方法: Windows フォーム MonthCalendar コントロールの外観を変更します。](how-to-change-monthcalendar-control-appearance.md)
