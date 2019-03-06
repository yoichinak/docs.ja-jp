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
ms.openlocfilehash: d72aef8a1328742f0b04c2ad009126e21390398a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367207"
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
