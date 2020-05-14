---
title: 動的オブジェクトの使用
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 20d007fb48e1db352bab6d8e25d2e60e02554732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345175"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>動的オブジェクトの使用 (Visual Basic)
動的オブジェクトを使用すると、`Object` 型とは別に、実行時にオブジェクトへの遅延バインディングを行うことができます。 動的オブジェクトは、<xref:System.Dynamic> 名前空間で定義されている動的インターフェイスを使用して、プロパティやメソッドなどのメンバーを実行時に公開します。 <xref:System.Dynamic> 名前空間のクラスを使用することで、静的な型や書式に一致しないデータ構造を操作するオブジェクトオブジェクトを作成できます。 また、IronPython や IronRuby などの動的言語で定義された動的オブジェクトを使用することもできます。 動的言語の作成方法の例、および動的言語で定義された動的オブジェクトの使用例については、[動的オブジェクトの作成と使用のチュートリアル](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、<xref:System.Dynamic.DynamicObject>、または <xref:System.Dynamic.ExpandoObject> に関するページを参照してください。  
  
 Visual Basic では、動的言語ランタイムおよび動的言語 (IronPython や IronRuby など) からオブジェクトへのバインドは、<xref:System.Dynamic.IDynamicMetaObjectProvider> インターフェイスを使用して行われます。 `IDynamicMetaObjectProvider` インターフェイスを実装したクラスの例としては、<xref:System.Dynamic.DynamicObject> や <xref:System.Dynamic.ExpandoObject> があります。  
  
 `IDynamicMetaObjectProvider` インターフェイスを実装したオブジェクトに対して遅延バインディングによる呼び出しが行われると、Visual Basic はそのインターフェイスを使用して動的オブジェクトにバインドします。 `IDynamicMetaObjectProvider` インターフェイスを実装していないオブジェクトに対して遅延バインディングによる呼び出しが行われた場合、または `IDynamicMetaObjectProvider` インターフェイスに対する呼び出しが失敗した場合は、Visual Basic は Visual Basic ランタイムの遅延バインディング機能を使用してオブジェクトにバインドします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [チュートリアル: 動的オブジェクトの作成と使用](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
