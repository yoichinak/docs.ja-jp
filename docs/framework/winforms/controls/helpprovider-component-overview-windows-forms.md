---
title: HelpProvider コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: cefc590bb3011b282392504a78ac5c393c58493e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965695"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider コンポーネントの概要 (Windows フォーム)
Windows フォーム[HelpProvider](helpprovider-component-windows-forms.md)コンポーネントは、Windows アプリケーションと共に html ヘルプ1.x ヘルプファイル (Html ヘルプワークショップで生成された .chm ファイル、または .htm ファイル) を関連付けるために使用されます。 ヘルプは、次のさまざまな方法で提供できます。  
  
- Windows フォームのコントロールについて、状況依存のヘルプを提供します。  
  
- ダイアログボックスの特定のダイアログボックスまたは特定のコントロールについて、状況依存のヘルプを提供します。  
  
- 目次のメインページ、インデックス、検索機能など、特定の領域に対してヘルプファイルを開きます。  
  
## <a name="using-the-help-provider"></a>ヘルププロバイダーの使用  
 Windows フォーム<xref:System.Windows.Forms.HelpProvider>にコンポーネントを追加すると、フォーム上の他のコントロールが<xref:System.Windows.Forms.HelpProvider>コンポーネントのヘルププロパティを公開できるようになります。 これにより、Windows フォーム上のコントロールにヘルプを提供できます。 プロパティを使用して、ヘルプファイル<xref:System.Windows.Forms.HelpProvider>をコンポーネントに関連付けることができます。 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> を呼び出し<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> 、指定したコントロールの<xref:System.Windows.Forms.HelpNavigator>列挙体の値を指定して、提供されるヘルプの種類を指定します。 ヘルプのキーワードまたはトピックは、 <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>メソッドを呼び出すことによって指定します。  
  
 必要に応じて、特定のヘルプ文字列を別のコントロールに<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>関連付けるには、メソッドを使用します。 コントロールにフォーカスがあるときにユーザーが F1 キーを押すと、このメソッドを使用してコントロールに関連付ける文字列がポップアップウィンドウに表示されます。  
  
 が<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>設定されていない場合は<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> 、を使用してヘルプテキストを指定する必要があります。 との両方<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>のヘルプ文字列を設定している場合は<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> 、に基づくヘルプが優先されます。  
  
> [!NOTE]
> コントロールの<xref:System.Windows.Forms.Help.ShowHelp%2A>メソッドまたは<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>プロパティでヘルプファイルへのパスを指定するときに、相対パスを使用すると問題が発生することがあります。 <xref:System.Windows.Forms.HelpProvider> そのため、絶対ファイルパスを使用してヘルプファイルを指定してください。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム アプリケーションのヘルプ システム](../advanced/help-systems-in-windows-forms-applications.md)
