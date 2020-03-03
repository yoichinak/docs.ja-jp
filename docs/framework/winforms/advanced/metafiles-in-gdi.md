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
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504593"
---
# <a name="metafiles-in-gdi"></a>GDI+ でのメタファイル
GDI + は、提供、<xref:System.Drawing.Imaging.Metafile>クラスに記録し、メタファイルを表示できます。 ベクター イメージとも呼ばれる、メタファイルは、一連の描画コマンドと設定として格納されているイメージです。 コマンドおよび設定に記録する<xref:System.Drawing.Imaging.Metafile>オブジェクトをメモリに格納されているか、ファイルまたはストリームに保存します。  
  
## <a name="metafile-formats"></a>メタファイル形式  
 GDI + は、次の形式で格納されているメタファイルを表示できます。  
  
- Windows メタファイル (WMF)  
  
- 拡張メタファイル (EMF)  
  
- EMF +  
  
 GDI + を記録できますメタファイル WMF 形式ではなく、EMF、EMF + 形式にします。  
  
 EMF + GDI + レコードを格納することができる EMF の拡張機能です。 EMF + 形式の 2 つのバリエーションがあります。EMF + のみと EMF + Dual します。 メタファイル EMF + だけでは、GDI + レコードだけが含まれます。 GDI + では、GDI ではなく、このようなメタファイルを表示できます。 EMF + Dual メタファイルには、GDI + と GDI レコードが含まれます。 EMF + Dual メタファイルに各の GDI + レコードは、代替 GDI レコードと組み合わせて使用します。 このようなメタファイルは、GDI または GDI + によって表示できます。  
  
 次の例では、ファイルとして保存された以前メタファイルを表示します。 左上隅にあるとメタファイルが表示されます (100, 100)。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
