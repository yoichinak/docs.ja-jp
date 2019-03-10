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
ms.openlocfilehash: 61a8d4baba35a7a8a8ae221b054029eb59107d0e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716258"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider コンポーネントの概要 (Windows フォーム)
Windows フォーム[ErrorProvider](errorprovider-component-windows-forms.md)コンポーネントは、フォームまたはコントロールのユーザー入力を検証するために使用します。 通常、フォーム上のユーザー入力の検証またはデータセット内のエラーを表示すると組み合わせて使用されます。 エラー プロバイダーでは、メッセージ ボックスでは、エラー メッセージを表示するよりも優れた選択肢は、エラー メッセージが表示されなくなった後、メッセージ ボックスを閉じると、ためです。 <xref:System.Windows.Forms.ErrorProvider>コンポーネントには、エラー アイコンが表示されます (![ErrorProvider アイコン](./media/vberrorprovidericon.gif "vbErrorProviderIcon"))、テキスト ボックスには、ユーザーが上にマウス ポインターを置いたときなど、関連するコントロールの横にある、エラー アイコンが、ツールヒントを表示、エラー メッセージ文字列を表示します。  
  
## <a name="key-properties"></a>キー プロパティ  
 <xref:System.Windows.Forms.ErrorProvider>コンポーネントのプロパティは<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>、 <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>、および<xref:System.Windows.Forms.ErrorProvider.Icon%2A>します。 使用する場合<xref:System.Windows.Forms.ErrorProvider>コンポーネント、データ バインド コントロールを<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>プロパティは、フォームのエラー アイコンを表示するコンポーネントの順序で適切なコンテナー (通常は Windows フォーム) に設定する必要があります。 デザイナーでコンポーネントが追加されたときに、<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>プロパティが格納されているフォーム; 場合、コードでコントロールを追加する必要があります、自分で設定しました。  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A>プロパティは、既定ではなく独自のエラー アイコンに設定することができます。 ときに、<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>プロパティが設定されて、<xref:System.Windows.Forms.ErrorProvider>コンポーネントは、データセットのエラー メッセージを表示できます。 重要なメソッド、<xref:System.Windows.Forms.ErrorProvider>コンポーネントは、<xref:System.Windows.Forms.ErrorProvider.SetError%2A>メソッド、エラー メッセージ文字列を指定して、エラー アイコンが表示されます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider>コンポーネントがユーザー補助クライアントの組み込みサポートを提供していません。 アプリケーションにアクセスできるようにする場合、このコンポーネントを使用してには、追加、アクセス可能なフィードバック メカニズムを提供する必要があります。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ErrorProvider>
- [方法: Windows フォーム ErrorProvider コンポーネントで DataSet 内のエラーの表示](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [方法: Windows フォーム ErrorProvider コンポーネントを使用してフォーム検証のエラー アイコンを表示します。](display-error-icons-for-form-validation-with-wf-errorprovider.md)
