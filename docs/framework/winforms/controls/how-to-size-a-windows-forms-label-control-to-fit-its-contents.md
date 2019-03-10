---
title: '方法: 内容に合わせて Windows フォーム Label コントロールをサイズします。'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 5771b232d77e3e5a792b179ebffd3fa0edda7c9b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702195"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>方法: 内容に合わせて Windows フォーム Label コントロールをサイズします。
Windows フォーム<xref:System.Windows.Forms.Label>コントロールは 1 行または複数の行であることができ、自動的にサイズを変更できる自体のキャプションを対応するために、サイズか固定できます。 <xref:System.Windows.Forms.Label.AutoSize%2A>プロパティは、大きくまたは小さくのキャプションに合わせてコントロールのサイズをこれには、実行時に、キャプションが変更される場合に特に便利です。  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>内容に合わせて動的にサイズを変更するラベル コントロールを作成するには  
  
1.  設定の<xref:System.Windows.Forms.Label.AutoSize%2A>プロパティを`true`します。  
  
 場合<xref:System.Windows.Forms.Label.AutoSize%2A>に設定されている`false`、指定した単語、<xref:System.Windows.Forms.Label.Text%2A>プロパティは、可能であれば、次の行に折り返されますが、コントロールは拡張されません。  
  
## <a name="see-also"></a>関連項目
- [方法: Windows フォームの Label コントロールでのアクセス キーを作成します。](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Label コントロールの概要](label-control-overview-windows-forms.md)
- [Label コントロール](label-control-windows-forms.md)
