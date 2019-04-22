---
title: 動的オブジェクトの使用 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: ea7d7aae1cd79a0243a9c721b5e3958fba82f84f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832074"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>動的オブジェクトの使用 (Visual Basic)
動的オブジェクトが他にも別の方法を提供、`Object`実行時にオブジェクトに遅延バインディングの種類。 動的オブジェクトで定義されている動的インターフェイスを使用して実行時のプロパティやメソッドなどのメンバーを公開します、<xref:System.Dynamic>名前空間。 クラスを使用することができます、<xref:System.Dynamic>名前空間を静的な型または形式が一致しないデータ構造を操作するオブジェクトを作成します。 IronPython や IronRuby などの動的言語で定義されている動的オブジェクトを使用することもできます。 動的オブジェクトを作成したり、動的言語で定義されている動的オブジェクトを使用する方法を示す例については、次を参照してください。[チュートリアル。動的オブジェクトの作成と](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、 <xref:System.Dynamic.DynamicObject>、または<xref:System.Dynamic.ExpandoObject>します。  
  
 Visual Basic のオブジェクトへのバインド、動的言語ランタイムと動的言語 IronPython や IronRuby などを使用して、<xref:System.Dynamic.IDynamicMetaObjectProvider>インターフェイス。 実装するクラスの例については、`IDynamicMetaObjectProvider`インターフェイスは、<xref:System.Dynamic.DynamicObject>と<xref:System.Dynamic.ExpandoObject>クラス。  
  
 実装するオブジェクトを遅延バインディング呼び出しが行われたかどうか、`IDynamicMetaObjectProvider`インターフェイス、そのインターフェイスを使用して、動的オブジェクトを Visual Basic をバインドします。 実装しないオブジェクトを遅延バインディング呼び出しが行われた場合、`IDynamicMetaObjectProvider`インターフェイス、または場合への呼び出し、`IDynamicMetaObjectProvider`インターフェイスが失敗した場合、Visual Basic が Visual Basic ランタイムの遅延バインディング機能を使用して、オブジェクトにバインドします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [チュートリアル: 動的オブジェクトの作成と使用](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
