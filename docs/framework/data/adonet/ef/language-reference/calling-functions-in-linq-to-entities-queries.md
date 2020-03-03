---
title: LINQ to Entities クエリ内の関数の呼び出し
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 267bb393d9e75c66eb18139e8897da34bd86e159
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251261"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>LINQ to Entities クエリ内の関数の呼び出し
このセクションの各トピックでは、LINQ to Entities クエリで関数を呼び出す方法について説明します。  
  
 <xref:System.Data.Objects.EntityFunctions> クラスおよび <xref:System.Data.Objects.SqlClient.SqlFunctions> クラスを使用すると、Entity Framework の一部として正規関数およびデータベース関数にアクセスできます。 詳細については、「[方法 :正規関数](how-to-call-canonical-functions.md)を呼び出し[、次の方法を実行します。データベース関数](how-to-call-database-functions.md)を呼び出します。  
  
 カスタム関数を呼び出すプロセスには、3 つの基本的な手順が必要です。  
  
1. 概念モデルで関数を定義するか、ストレージ モデルで関数を宣言します。  
  
2. メソッドをアプリケーションに追加し、<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> を使用してこれをモデルの関数にマップします。  
  
3. LINQ to Entities クエリから関数を呼び出します。  
  
 詳細については、このセクションの各トピックを参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 正規関数を呼び出す](how-to-call-canonical-functions.md)  
  
 [方法: データベース関数の呼び出し](how-to-call-database-functions.md)  
  
 [方法: カスタムデータベース関数を呼び出す](how-to-call-custom-database-functions.md)  
  
 [方法: クエリでモデル定義関数を呼び出す](how-to-call-model-defined-functions-in-queries.md)  
  
 [方法: モデル定義関数をオブジェクトメソッドとして呼び出す](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>関連項目

- [LINQ to Entities でのクエリ](queries-in-linq-to-entities.md)
- [正規関数](canonical-functions.md)
- [.edmx ファイルの概要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [方法: 概念モデルでカスタム関数を定義する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
