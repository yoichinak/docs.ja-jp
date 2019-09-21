---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 4995512336ee9eb6e33df011757ed533db57e76e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783789"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
LINQ to DataSet を使用すると、オブジェクトにキャッシュされた<xref:System.Data.DataSet>データに対するクエリを簡単かつ迅速に行うことができます。 具体的には、LINQ to DataSet は、開発者が個別のクエリ言語を使用するのではなく、プログラミング言語自体からクエリを作成できるようにすることで、クエリを簡略化します。 これは、visual studio 開発者にとって特に便利です。これにより、Visual Studio がクエリで提供するコンパイル時の構文チェック、静的な型指定、IntelliSense サポートを利用できるようになりました。  
  
 また、LINQ to DataSet を使用して、1つまたは複数のデータソースから統合されたデータを照会することもできます。 これにより、ローカルに集計されたデータのクエリや Web アプリケーションでの中間層のキャッシュなど、データの表現方法や扱いに柔軟性が要求されるさまざまなシナリオが実現します。 特に、汎用のレポート作成、分析、ビジネス インテリジェンスを行うアプリケーションでは、この手法を用いたデータ操作が欠かせません。  
  
 LINQ to DataSet 機能は、主におよび<xref:System.Data.DataRowExtensions> <xref:System.Data.DataTableExtensions>クラスの拡張メソッドを通じて公開されます。 LINQ to DataSet は、既存の ADO.NET アーキテクチャを使用してをビルドし、アプリケーションコードの ADO.NET を置き換えることを意図していません。 既存の ADO.NET コードは、LINQ to DataSet アプリケーションで引き続き機能します。 次の図は、ADO.NET とデータストアの LINQ to DataSet の関係を示しています。  
  
 ![LINQ to DataSet が ADO.NET プロバイダーに基づいていることを示す図。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](getting-started-linq-to-dataset.md)  
  
 [プログラミング ガイド](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>参照  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>関連項目

- [統合言語クエリ (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [統合言語クエリ (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ と ADO.NET](linq-and-ado-net.md)
- [ADO.NET](index.md)
