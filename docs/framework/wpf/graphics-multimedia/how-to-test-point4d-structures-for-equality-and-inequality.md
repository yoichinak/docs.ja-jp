---
title: '方法: Point4D 構造体が等価かどうかをテストする'
ms.date: 03/30/2017
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
ms.openlocfilehash: ce1188e99ef2b0682427cc2e227aaccd27f7c4f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198440"
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a>方法: Point4D 構造体が等価かどうかをテストする
この例は、テストする方法を示しています。<xref:System.Windows.Media.Media3D.Point4D>構造体が等しいかどうか。  
  
 次のコードをテストする方法を示しています。<xref:System.Windows.Media.Media3D.Point4D>構造体が等しいかどうかと非等値を使用して、<xref:System.Windows.Media.Media3D.Point4D>等しいかどうかの方法です。  <xref:System.Windows.Media.Media3D.Point4D>オーバー ロードされた等値を使用して等しいかどうかの構造を検査 (`==`) 演算子をオーバー ロードされた不等値を使用して非等値の (`!=`) 演算子、および最後に、<xref:System.Windows.Media.Media3D.Point3D>構造と<xref:System.Windows.Media.Media3D.Point4D>構造体は、静的 using に等しいかどうかチェックされます<xref:System.Windows.Media.Media3D.Point4D.Equals%2A>メソッド。  
  
## <a name="example"></a>例  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
