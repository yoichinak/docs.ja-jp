---
title: ErrorProvider コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: 3cfd3f306d4a18ce8a194b5197060fbca1d157d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965293"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider コンポーネントの概要 (Windows フォーム)
Windows フォーム[ErrorProvider](errorprovider-component-windows-forms.md)コンポーネントは、フォームまたはコントロールのユーザー入力を検証するために使用されます。 通常は、フォームでのユーザー入力の検証、またはデータセット内のエラーの表示と組み合わせて使用されます。 エラープロバイダーは、メッセージボックスにエラーメッセージを表示するよりも適しています。これは、メッセージボックスが閉じられると、エラーメッセージが表示されなくなるためです。 コンポーネント<xref:System.Windows.Forms.ErrorProvider>は、テキストボックスなど、![関連するコントロールの横にエラーアイコン (](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)赤い丸の内側に白い感嘆符) を表示します。ユーザーがマウスポインターをエラーアイコンの上に置くと、ツールヒントが表示されます。エラーメッセージ文字列を表示しています。  
  
## <a name="key-properties"></a>キー プロパティ  
 コンポーネントのキープロパティは<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>、 <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>、、および<xref:System.Windows.Forms.ErrorProvider.Icon%2A>です。 <xref:System.Windows.Forms.ErrorProvider> データバインド<xref:System.Windows.Forms.ErrorProvider>コントロール<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>でコンポーネントを使用する場合は、コンポーネントがフォームにエラーアイコンを表示するために、プロパティを適切なコンテナー (通常は Windows フォーム) に設定する必要があります。 コンポーネントがデザイナー <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>に追加されると、プロパティは、それを含んでいるフォームに設定されます。コントロールをコードに追加する場合は、自分で設定する必要があります。  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A>プロパティは、既定のの代わりにカスタムエラーアイコンに設定できます。 プロパティが設定されている<xref:System.Windows.Forms.ErrorProvider>場合、コンポーネントはデータセットのエラーメッセージを表示できます。 <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> <xref:System.Windows.Forms.ErrorProvider>コンポーネントの主要<xref:System.Windows.Forms.ErrorProvider.SetError%2A>なメソッドは、エラーメッセージ文字列を指定し、エラーアイコンが表示されるメソッドです。  
  
> [!NOTE]
> コンポーネント<xref:System.Windows.Forms.ErrorProvider>には、ユーザー補助クライアントの組み込みサポートが用意されていません。 このコンポーネントを使用してアプリケーションにアクセスできるようにするには、追加のアクセス可能なフィードバックメカニズムを提供する必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ErrorProvider>
- [方法: Windows フォーム ErrorProvider コンポーネントを使用してデータセット内のエラーを表示する](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [方法: Windows フォーム ErrorProvider コンポーネントを使用したフォーム検証のエラーアイコンの表示](display-error-icons-for-form-validation-with-wf-errorprovider.md)
