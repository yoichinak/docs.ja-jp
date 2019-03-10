---
title: '方法: インストールされたデコーダーの一覧'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: c40bb79dde4a9baf8b84f3cda5fdabc6e30ad0b5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717532"
---
# <a name="how-to-list-installed-decoders"></a>方法: インストールされたデコーダーの一覧
アプリケーションが特定のイメージ ファイル形式を読み取るかどうかを判断するコンピューターでは、使用可能なイメージ デコーダーの一覧を表示することがあります。 <xref:System.Drawing.Imaging.ImageCodecInfo>クラスには、<xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>静的メソッド イメージ デコーダーは、使用可能なを確認できるようにします。 <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> 配列を返します<xref:System.Drawing.Imaging.ImageCodecInfo>オブジェクト。  
  
## <a name="example"></a>例  
 次のコード例では、インストールされたデコーダーの一覧とそのプロパティ値を出力します。  
  
 [!code-csharp[UsingImageEncodersDecoders#2](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   Windows フォーム アプリケーション  
  
-   A<xref:System.Windows.Forms.PaintEventArgs>はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目
- [方法: インストールされたエンコーダーの一覧](how-to-list-installed-encoders.md)
- [マネージド GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用](using-image-encoders-and-decoders-in-managed-gdi.md)
