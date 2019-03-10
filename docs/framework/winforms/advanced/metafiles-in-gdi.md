---
title: GDI+ でのメタファイル
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: 25ce3fdd98560aba0918431bb77d6f3f23a04784
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722465"
---
# <a name="metafiles-in-gdi"></a>GDI+ でのメタファイル
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供、<xref:System.Drawing.Imaging.Metafile>クラスに記録し、メタファイルを表示できます。 ベクター イメージとも呼ばれる、メタファイルは、一連の描画コマンドと設定として格納されているイメージです。 コマンドおよび設定に記録する<xref:System.Drawing.Imaging.Metafile>オブジェクトをメモリに格納されているか、ファイルまたはストリームに保存します。  
  
## <a name="metafile-formats"></a>メタファイル形式  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 次の形式で格納されているメタファイルを表示できます。  
  
-   Windows メタファイル (WMF)  
  
-   拡張メタファイル (EMF)  
  
-   EMF +  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] WMF の形式ではなく、EMF、EMF + 形式には、メタファイルを記録できます。  
  
 EMF + は、拡張機能により、EMF[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]レコードが格納されます。 EMF + 形式の 2 つのバリエーションがあります。EMF + のみと EMF + Dual します。 メタファイル EMF + だけしか[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]レコード。 このようなメタファイルで表示できる[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]がなく、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]します。 EMF + Dual メタファイルを含む[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]レコード。 各[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]EMF + Dual レコード メタファイルとペアになって、代替[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]レコード。 このようなメタファイルで表示できる[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]または[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]します。  
  
 次の例では、ファイルとして保存された以前メタファイルを表示します。 左上隅にあるとメタファイルが表示されます (100, 100)。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>関連項目
- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
