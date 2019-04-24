---
title: '方法: Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: 08d5a505229cd434dbf82e8ae4624bb418efd379
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335941"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>方法: Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する
Windows フォーム<xref:System.Windows.Forms.DateTimePicker>柔軟にコントロールで日付と時刻の表示の書式設定を制御します。 <xref:System.Windows.Forms.DateTimePicker.Format%2A>プロパティに表示される定義済みの形式から選択することができます、<xref:System.Windows.Forms.DateTimePickerFormat>します。 形式指定文字を使用して、独自の書式スタイルを作成するには、目的のための適切な場合、これらのいずれも<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>します。  
  
### <a name="to-display-a-custom-format"></a>カスタム形式を表示するには  
  
1. <xref:System.Windows.Forms.DateTimePicker.Format%2A> プロパティを `DateTimePickerFormat.Custom` に設定します。  
  
2. 設定、<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>プロパティを書式指定文字列。  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a>テキスト書式設定された値を追加するには  
  
1. "M"のような書式指定文字またはなどの区切り記号以外の任意の文字を囲む単一引用符を使用して":"です。 たとえば、次の書式指定文字列には、形式で現在の日付が表示されます。"今日は。05時 30分: 31 金曜日 March 02、2012"英語 (米国) カルチャ。  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     カルチャの設定に応じて単一引用符で囲まれていない文字は変更される可能性があります。 たとえば、上記の書式指定文字列には、形式の現在の日付が表示されます。"今日は。05時 30分: 31 金曜日 March 02、2012"英語 (米国) カルチャ。 "Hh:mm:ss"であるため、区切り記号をするものではありませんので、最初のコロンが単一引用符で囲まれていることに注意してください。 別のカルチャでは、形式がありますとして表示されます"今日は。05.30.31 金曜日 March 02、2012"。  
  
## <a name="see-also"></a>関連項目

- [DateTimePicker コントロール](datetimepicker-control-windows-forms.md)
- [方法: Windows フォームの DateTimePicker コントロールを設定し、戻り値の日付](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
