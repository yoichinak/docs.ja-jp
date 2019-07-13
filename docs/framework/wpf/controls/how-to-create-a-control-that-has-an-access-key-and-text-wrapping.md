---
title: '方法: アクセス キーおよびテキスト折り返し機能を持つコントロールを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: 48e439719afa2426b5d8f822c621080cdc32514e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910924"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a>方法: アクセス キーおよびテキスト折り返し機能を持つコントロールを作成する
この例では、アクセス キーがありテキスト折り返しをサポートするコントロールを作成する方法を説明します。 この例では、<xref:System.Windows.Controls.Label>これらの概念を説明するコントロール。  
  
## <a name="example"></a>例  
 **ラベルにテキスト折り返し機能を追加する**  
  
 <xref:System.Windows.Controls.Label>コントロールはテキスト折り返し機能をサポートしていません。 複数の行を折り返せるラベルが必要な場合には、テキスト折り返し機能をサポートしている別の要素を入れ子にすることができます。 次の例は、使用する方法を示します、<xref:System.Windows.Controls.TextBlock>複数行のテキストをラップするラベルを作成します。  
  
 [!code-xaml[LabelSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **アクセス キーおよびテキスト折り返し機能をラベルに追加する**  
  
 必要がある場合、<xref:System.Windows.Controls.Label>アクセス キー (ニーモニック) を持つを使用して、<xref:System.Windows.Controls.AccessText>要素内にある、<xref:System.Windows.Controls.Label>します。  
  
 などのコントロール<xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.RadioButton>、 <xref:System.Windows.Controls.CheckBox>、 <xref:System.Windows.Controls.MenuItem>、 <xref:System.Windows.Controls.TabItem>、 <xref:System.Windows.Controls.Expander>、および<xref:System.Windows.Controls.GroupBox>コントロールの既定のテンプレートがあります。 これらのテンプレートに含まれる、<xref:System.Windows.Controls.ContentPresenter>します。 設定できるプロパティの 1 つ、<xref:System.Windows.Controls.ContentPresenter>は<xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true"、コントロールのアクセス キーを指定するのに使用できます。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.Label>をアクセス キーし、テキストの折り返しをサポートしています。 テキストの折り返しを例のセットを有効にする、<xref:System.Windows.Controls.AccessText.TextWrapping%2A>プロパティでは下線がアクセス キーを指定する文字します。 (下線文字の直後の文字はアクセス キーになります。)  
  
 [!code-xaml[LabelSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a>関連項目

- [方法: ラベルのターゲット プロパティを設定します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752101(v=vs.90))
