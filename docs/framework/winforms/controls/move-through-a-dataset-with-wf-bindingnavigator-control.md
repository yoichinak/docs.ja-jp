---
title: '方法: Windows フォームの BindingNavigator コントロールを使用して DataSet を移動する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d33cad4d0a60aa29d8c9f5e2217532963e8358c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952694"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a>方法: Windows フォームの BindingNavigator コントロールを使用して DataSet を移動する
データ ドリブン アプリケーションを作成するときに、ユーザーにデータのコレクションを表示する必要がある場合があります。 <xref:System.Windows.Forms.BindingNavigator> コントロールは、<xref:System.Windows.Forms.BindingSource> コンポーネントと組み合わせて、コレクションを移動して項目を順番に表示する、便利で拡張可能なソリューションを提供します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Forms.BindingNavigator> コントロールを使用してデータ間を移動する方法を、次のコード例に示します。 セットは <xref:System.Data.DataView> に含まれ、<xref:System.Windows.Forms.BindingSource> コンポーネントを持つ <xref:System.Windows.Forms.TextBox> コントロールにバインドされます。  
  
> [!NOTE]
> 接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System、System.Data、System.Drawing、System.Windows.Forms、および System.Xml アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator コントロール](bindingnavigator-control-windows-forms.md)
- [BindingSource コンポーネント](bindingsource-component.md)
- [方法: Windows フォームコントロールを型にバインドする](how-to-bind-a-windows-forms-control-to-a-type.md)
