---
title: エンコード方式および Windows フォームのグローバリゼーション
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
ms.openlocfilehash: 3a9d891fe898cf691a5f0d36e6360c2a73fb199d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629230"
---
# <a name="encoding-and-windows-forms-globalization"></a>エンコード方式および Windows フォームのグローバリゼーション
Windows フォーム アプリケーションは、Unicode に完全対応しているため、プラットフォーム、プログラム、または言語に関係なく、文字がそれぞれ一意の数字で表されます。 Unicode の詳細については、、 [Unicode consortium Web サイト](https://www.unicode.org)を参照してください。  
  
## <a name="benefits-of-unicode"></a>Unicode の利点  
 Unicode 対応フォームの利点として、ヒンディー語などの Unicode 専用のスクリプトを操作できる点も含まれます。 さらに、1 つのフォームで複数の言語を使用できます。 Unicode では、すべての文字が 2 バイト長なので、2 バイト文字を表すために特別な作業は必要ありません。 また、すべてのプラットフォームで動作する 1 つのコードのセットを作成することもできます。 これは以前のバージョンの Visual Basic では、Windows NT などのさまざまなプラットフォーム向けのさまざまなコードを記述する必要があるからの変更と[!INCLUDE[win98](../../../../includes/win98-md.md)]します。  
  
 ただし、[!INCLUDE[win98](../../../../includes/win98-md.md)] および Windows Millennium Edition では、特定のコントロールが Unicode をサポートしません。 これらのコントロールはすべてコモン コントロールから継承されていて、Windows コード ページで [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)] としてデータを処理します。 これらのコントロールは、<xref:System.Windows.Forms.TabControl>、<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.DateTimePicker>、<xref:System.Windows.Forms.MonthCalendar>、<xref:System.Windows.Forms.TrackBar>、<xref:System.Windows.Forms.ProgressBar>、<xref:System.Windows.Forms.ImageList>、<xref:System.Windows.Forms.ToolBar>、および <xref:System.Windows.Forms.StatusBar> です。 その結果、前述のプラットフォーム上のこれらのコントロールで Unicode データを表示することはできません。 たとえば、日本語の文字を英語の [!INCLUDE[win98](../../../../includes/win98-md.md)] オペレーティング システムで表示することはできません。  
  
 <xref:System.Windows.Forms.ToolBar> コントロールと <xref:System.Windows.Forms.StatusBar> コントロールの Unicode 対応の代替手段として、これらの古いコントロールを置換する <xref:System.Windows.Forms.ToolStrip> コントロールと <xref:System.Windows.Forms.StatusStrip> コントロールを使用します。 アプリケーションの視覚要素の間で同様のルック アンド フィールを維持するには、メニューの表示に <xref:System.Windows.Forms.MainMenu> の代わりに <xref:System.Windows.Forms.MenuStrip> コントロールを使用します。 <xref:System.Windows.Forms.ToolStrip> と <xref:System.Windows.Forms.StatusStrip> のように、<xref:System.Windows.Forms.MenuStrip> も Unicode 文字を処理して表示することができます。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム アプリケーションのグローバル化](globalizing-windows-forms.md)
