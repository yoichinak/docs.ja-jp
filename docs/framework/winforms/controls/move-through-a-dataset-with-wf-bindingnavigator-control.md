---
title: '方法: Windows フォームの BindingNavigator コントロールを使用して DataSet を移動します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d8db965993e82040cfe88c22aaabfaed21462a40
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709754"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a>方法: Windows フォームの BindingNavigator コントロールを使用して DataSet を移動します。
データ ドリブン アプリケーションを作成するときに、ユーザーにデータのコレクションを表示する必要がある場合があります。 <xref:System.Windows.Forms.BindingNavigator> コントロールは、<xref:System.Windows.Forms.BindingSource> コンポーネントと組み合わせて、コレクションを移動して項目を順番に表示する、便利で拡張可能なソリューションを提供します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Forms.BindingNavigator> コントロールを使用してデータ間を移動する方法を、次のコード例に示します。 セットは <xref:System.Data.DataView> に含まれ、<xref:System.Windows.Forms.BindingSource> コンポーネントを持つ <xref:System.Windows.Forms.TextBox> コントロールにバインドされます。  
  
> [!NOTE]
>  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、System.Windows.Forms、および System.Xml アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual c# の構築方法の詳細については、[、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator コントロール](bindingnavigator-control-windows-forms.md)
- [BindingSource コンポーネント](bindingsource-component.md)
- [方法: Windows フォーム コントロールを型にバインドします。](how-to-bind-a-windows-forms-control-to-a-type.md)
