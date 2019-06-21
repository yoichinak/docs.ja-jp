---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 36335f90c7850fa00a15e7112b7473637250c656
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306244"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] は、<xref:System.Data.DataSet> オブジェクトにキャッシュされたデータに対するクエリをより簡単に、より高速にします。 具体的には、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]個別のクエリ言語を使用して、クエリの代わりに、プログラミング言語そのものを記述できるので、クエリを簡略化します。 これは、コンパイル時の構文チェック、静的な型指定、およびそのクエリで Visual Studio によって提供される IntelliSense サポートのメリットを得ることができます、Visual Studio 開発者に特に便利です。  
  
 また、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使用すると、1 つまたは複数のデータ ソースから取得して統合したデータを照会することもできます。 これにより、ローカルに集計されたデータのクエリや Web アプリケーションでの中間層のキャッシュなど、データの表現方法や扱いに柔軟性が要求されるさまざまなシナリオが実現します。 特に、汎用のレポート作成、分析、ビジネス インテリジェンスを行うアプリケーションでは、この手法を用いたデータ操作が欠かせません。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]機能は、拡張メソッドによって主に公開されて、<xref:System.Data.DataRowExtensions>と<xref:System.Data.DataTableExtensions>クラス。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ビルドし、既存の ADO.NET アーキテクチャを使用してアプリケーション コードで ADO.NET を置換するものではありません。 既存の ADO.NET コードは引き続き機能で、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]アプリケーション。 リレーションシップの[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]ADO.NET データとストアは次の図に示します。  
  
 ![LINQ to DataSet が ADO.NET プロバイダーに基づくされていることを示す図。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [プログラミング ガイド](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>参照  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>関連項目

- [統合言語クエリ (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [統合言語クエリ (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ と ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
