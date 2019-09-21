---
title: ユーザー定義関数
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 40697da4fe678668f8f7ecda86abebf40da7b973
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792303"
---
# <a name="user-defined-functions"></a>ユーザー定義関数
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、オブジェクト モデル内のメソッドを使用して、ユーザー定義関数を表します。 <xref:System.Data.Linq.Mapping.FunctionAttribute> 属性、および必要に応じて <xref:System.Data.Linq.Mapping.ParameterAttribute> 属性を適用することによって、メソッドを関数として指定します。 詳細については、「 [LINQ to SQL オブジェクトモデル](the-linq-to-sql-object-model.md)」を参照してください。  
  
 <xref:System.InvalidOperationException> を回避するため、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で作成するユーザー定義関数は次のいずれかの形式にする必要があります。  
  
- 正しいマッピング属性を持つメソッド呼び出しとしてラップされた関数。 詳細については、「[属性ベースのマッピング](attribute-based-mapping.md)」を参照してください。  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に固有の静的 SQL メソッド。  
  
- .NET Framework メソッドによってサポートされる関数。  
  
 このセクションのトピックでは、自分でコードを作成する場合に、アプリケーション内でこれらのメソッドを記述および呼び出す方法について説明します。 Visual Studio を使用する開発者は、通常、オブジェクトリレーショナルデザイナーを使用してユーザー定義関数をマップします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: スカラー値のユーザー定義関数を使用する](how-to-use-scalar-valued-user-defined-functions.md)  
 スカラー値を返す関数を実装する方法を説明します。  
  
 [方法: テーブル値ユーザー定義関数を使用する](how-to-use-table-valued-user-defined-functions.md)  
 テーブル値を返す関数を実装する方法を説明します。  
  
 [方法: ユーザー定義関数をインラインで呼び出す](how-to-call-user-defined-functions-inline.md)  
 関数をインラインで呼び出す方法とインライン呼び出しの実行時の相違点について説明します。
