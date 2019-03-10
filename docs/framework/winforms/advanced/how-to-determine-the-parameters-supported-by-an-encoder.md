---
title: '方法: エンコーダーがサポートするパラメーターを確認します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: f5af00833c8d8373444b475673709d902598d9d0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719703"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a>方法: エンコーダーがサポートするパラメーターを確認します。
品質と圧縮レベルでなどの画像のパラメーターを調整することができますが、パラメーターが指定したイメージ エンコーダーでサポートされているを知る必要があります。 <xref:System.Drawing.Image>クラスには、<xref:System.Drawing.Image.GetEncoderParameterList%2A>メソッドどのイメージ パラメーターを特定のエンコーダーのサポートを確認できるようにします。 GUID では、エンコーダーを指定します。 <xref:System.Drawing.Image.GetEncoderParameterList%2A>メソッドの配列を返します<xref:System.Drawing.Imaging.EncoderParameter>オブジェクト。  
  
## <a name="example"></a>例  
 次のコード例では、JPEG エンコーダーでサポートされているパラメーターを出力します。 パラメーターのカテゴリと関連付けられている Guid のリストを使用して、<xref:System.Drawing.Imaging.Encoder>各パラメーターのカテゴリを確認するクラスの概要。  
  
 [!code-csharp[UsingImageEncodersDecoders#3](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   Windows フォーム アプリケーション  
  
-   A<xref:System.Windows.Forms.PaintEventArgs>はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目
- [方法: インストールされたエンコーダーの一覧](how-to-list-installed-encoders.md)
- [ビットマップの種類](types-of-bitmaps.md)
- [マネージド GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用](using-image-encoders-and-decoders-in-managed-gdi.md)
