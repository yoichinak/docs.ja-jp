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
ms.openlocfilehash: 9e8dc2ee2773b26a7bfef1da209399a8b49de9ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624125"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider コンポーネントの概要 (Windows フォーム)
Windows フォーム[HelpProvider](helpprovider-component-windows-forms.md)に HTML ヘルプ 1.x のヘルプ ファイル (HTML Help Workshop で生成された .chm ファイル、または .htm ファイル) を Windows アプリケーションに関連付けるコンポーネントを使用します。 さまざまな方法でヘルプを行うことができます。  
  
- Windows フォームのコントロールには、状況依存のヘルプを提供します。  
  
- 特定のダイアログ ボックスまたはダイアログ ボックスの特定のコントロールでは、状況依存のヘルプを提供します。  
  
- テーブルの内容、インデックス、または検索関数のメイン ページなどの特定領域へのヘルプ ファイルを開きます。  
  
## <a name="using-the-help-provider"></a>ヘルプのプロバイダーを使用します。  
 追加、<xref:System.Windows.Forms.HelpProvider>を Windows フォームのコンポーネントは、のヘルプ プロパティを公開するフォーム上の他のコントロールを使用できます、<xref:System.Windows.Forms.HelpProvider>コンポーネント。 これにより、Windows フォーム上のコントロールのヘルプを提供することができます。 ヘルプ ファイルを関連付けることができます、<xref:System.Windows.Forms.HelpProvider>コンポーネントを使用して、<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>プロパティ。 呼び出すことによって提供されるヘルプの種類を指定する<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>から値を指定して、<xref:System.Windows.Forms.HelpNavigator>指定したコントロールの列挙体。 呼び出すことでヘルプのキーワードまたはトピックを提供する、<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>メソッド。  
  
 必要に応じて、特定のヘルプ文字列を別のコントロールに関連付けるに次のように使用します。、<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>メソッド。 このメソッドを使用するコントロールと関連付ける文字列は、コントロールにフォーカスがあるユーザーが F1 キーを押したときに、ポップアップ ウィンドウに表示されます。  
  
 場合<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>設定を使用する必要がありますが<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>ヘルプ テキストを提供します。 両方を設定している場合<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>およびヘルプ文字列、ヘルプに基づいて<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>が優先されます。  
  
> [!NOTE]
>  ヘルプ ファイルへのパスを指定するときに、相対パスを使用して問題が発生する可能性があります、<xref:System.Windows.Forms.Help.ShowHelp%2A>メソッドまたは<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>のプロパティ、<xref:System.Windows.Forms.HelpProvider>コントロール。 したがって、ファイルの絶対パスを使用してヘルプ ファイルを指定することを確認します。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム アプリケーションのヘルプ システム](../advanced/help-systems-in-windows-forms-applications.md)
