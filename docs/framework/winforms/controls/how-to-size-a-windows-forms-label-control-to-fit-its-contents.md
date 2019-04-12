---
title: '方法: Windows フォーム Label コントロールのサイズを内容に合わせて変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 110aab0c0826bb4b06e22158afd6af37b5406be4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312190"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>方法: Windows フォーム Label コントロールのサイズを内容に合わせて変更する
Windows フォーム<xref:System.Windows.Forms.Label>コントロールは 1 行または複数の行であることができ、自動的にサイズを変更できる自体のキャプションを対応するために、サイズか固定できます。 <xref:System.Windows.Forms.Label.AutoSize%2A>プロパティは、大きくまたは小さくのキャプションに合わせてコントロールのサイズをこれには、実行時に、キャプションが変更される場合に特に便利です。  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>内容に合わせて動的にサイズを変更するラベル コントロールを作成するには  
  
1. 設定の<xref:System.Windows.Forms.Label.AutoSize%2A>プロパティを`true`します。  
  
 場合<xref:System.Windows.Forms.Label.AutoSize%2A>に設定されている`false`、指定した単語、<xref:System.Windows.Forms.Label.Text%2A>プロパティは、可能であれば、次の行に折り返されますが、コントロールは拡張されません。  
  
## <a name="see-also"></a>関連項目

- [方法: Windows フォームの Label コントロールでアクセス キーを作成する](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Label コントロールの概要 (Windows フォーム)](label-control-overview-windows-forms.md)
- [Label コントロール](label-control-windows-forms.md)
