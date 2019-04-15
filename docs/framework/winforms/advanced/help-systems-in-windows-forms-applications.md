---
title: Windows フォーム アプリケーションのヘルプ システム
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
ms.openlocfilehash: 1a02271d59a59f0a6e06a652a34922ba5dcdf1f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087275"
---
# <a name="help-systems-in-windows-forms-applications"></a>Windows フォーム アプリケーションのヘルプ システム
1 つの最も重要な配慮をするように、アプリケーションの開発者は、ユーザーに提供できますが有能なヘルプ システムです。 これは、混乱または混乱になるときを有効にします。 使用して簡単に行うは、Windows ベースのアプリケーションにヘルプ システムを提供する、 [HelpProvider コンポーネント](../controls/helpprovider-component-windows-forms.md)します。  
  
## <a name="different-types-of-help"></a>さまざまな種類のヘルプ  
 Windows フォーム <xref:System.Windows.Forms.HelpProvider> コンポーネントは、Windows ベースのアプリケーションで HTML ヘルプ 1.x のヘルプ ファイル (HTML Help Workshop で生成された .chm ファイル、または .htm ファイル) を関連付けるために使用します。 <xref:System.Windows.Forms.HelpProvider>コンポーネントは、Windows フォーム上のコントロールまたはコントロールの特定の状況依存のヘルプを提供するために使用できます。 さらに、<xref:System.Windows.Forms.HelpProvider>コンポーネントは、コンテンツ、インデックス、または検索関数のテーブルのメイン ページなどの特定領域へのヘルプ ファイルを開くことができます。 概要については、<xref:System.Windows.Forms.HelpProvider>コンポーネントを参照してください[HelpProvider コンポーネントの概要](../controls/helpprovider-component-overview-windows-forms.md)します。 使用する方法については、 <xref:System.Windows.Forms.HelpProvider> 、Windows フォームのポップアップ ヘルプを表示するコンポーネントを参照してください[方法。ポップアップ ヘルプを表示](how-to-display-pop-up-help.md)します。 使用方法について、<xref:System.Windows.Forms.ToolTip>コントロールに固有のヘルプを表示するコンポーネントを参照してください[コントロール ヘルプを使用してツールヒント](control-help-using-tooltips.md)します。  
  
 HTML Help Workshop で HTML ヘルプ 1.x のファイルを生成することができます。 HTML ヘルプの詳細については、"HTML Help Workshop"または MSDN の他の"HTML"ヘルプ トピックを参照してください。  
  
## <a name="see-also"></a>関連項目

- [Windows フォームでのヘルプの統合](integrating-user-help-in-windows-forms.md)
- [HelpProvider コンポーネント](../controls/helpprovider-component-windows-forms.md)
- [ToolTip コンポーネント](../controls/tooltip-component-windows-forms.md)
- [Windows フォームの概要](../windows-forms-overview.md)
- [Windows フォーム](../index.md)
