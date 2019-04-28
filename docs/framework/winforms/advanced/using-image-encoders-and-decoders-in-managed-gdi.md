---
title: マネージド GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: bf0d3a64ce8860d67f0dcfd37c780f03fbd7471a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650519"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>マネージド GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用
<xref:System.Drawing>名前空間には、<xref:System.Drawing.Image>と<xref:System.Drawing.Bitmap>クラスを格納すると、画像を操作します。 イメージ エンコーダーを使用して[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、メモリからディスク イメージを記述することができます。 イメージのデコーダーを使用して[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、ディスクからイメージをメモリに読み込むことができます。 エンコーダーでデータを変換する、<xref:System.Drawing.Image>または<xref:System.Drawing.Bitmap>オブジェクトが指定されたディスク ファイルの形式に変換します。 デコーダーがディスク ファイルで必要な形式にデータを変換、<xref:System.Drawing.Image>と<xref:System.Drawing.Bitmap>オブジェクト。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 組み込みのエンコーダーとデコーダー ファイルの種類をサポートするには。  
  
- BMP  
  
- GIF  
  
- JPEG  
  
- PNG  
  
- TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 次のファイルの種類をサポートする組み込みのデコーダーがあります。  
  
- WMF  
  
- EMF  
  
- アイコン  
  
 次のトピックでは、エンコーダーとデコーダーの詳細について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: インストールされたエンコーダーの一覧](how-to-list-installed-encoders.md)  
 コンピューターで使用可能なエンコーダーの一覧を表示する方法について説明します。  
  
 [方法: インストールされたデコーダーの一覧](how-to-list-installed-decoders.md)  
 コンピューターで使用可能なデコーダーの一覧を表示する方法について説明します。  
  
 [方法: エンコーダーがサポートするパラメーターを確認します。](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 一覧表示する方法について説明します、<xref:System.Drawing.Imaging.EncoderParameters>エンコーダーがサポートされています。  
  
 [方法: BMP イメージを PNG イメージに変換します。](how-to-convert-a-bmp-image-to-a-png-image.md)  
 さまざまなイメージ形式でイメージを保存する方法について説明します。  
  
 [方法: JPEG 圧縮レベルの設定します。](how-to-set-jpeg-compression-level.md)  
 イメージの品質レベルを変更する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>関連項目  
 [GDI+ マネージド コードについて](about-gdi-managed-code.md)  
  
 [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
