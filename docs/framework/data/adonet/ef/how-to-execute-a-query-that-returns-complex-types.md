---
title: '方法: 複合型を返すクエリを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: a428f54c3834ccdf6a0c7a5bfce8307172724524
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607207"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>方法: 複合型を返すクエリを実行する
このトピックでは、複合型プロパティを含むエンティティ型オブジェクトを返す [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行する方法について説明します。  
  
### <a name="to-run-the-code-in-this-example"></a>この例のコードを実行するには  
  
1. 追加、 [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)をプロジェクトに使用するプロジェクトを構成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]します。 詳細については、「[方法 :エンティティ データ モデル ウィザードを使用して](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))します。  
  
2. アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. モデルを表示する .edmx ファイルをダブルクリック、[モデル ブラウザー ウィンドウ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100))エンティティ デザイナーの。 エンティティ デザイナー画面で選択、`Email`と`Phone`のプロパティ、`Contact`エンティティ型、し、右クリックして選択**新しい複合型へのリファクター**します。  
  
4. 選択した場合は、新しい複合型`Email`と`Phone`にプロパティを追加、**モデル ブラウザー**します。 複合型が既定の名前を指定: 型の名前を変更`EmailPhone`で、**プロパティ**ウィンドウ。 また、新しい `ComplexProperty` プロパティが `Contact` エンティティ型に追加されます。 プロパティの名前を `EmailPhoneComplexType.` に変更します。  
  
     作成して、Entity Data Model ウィザードを使用した複合型の変更については、次を参照してください。[方法。既存のプロパティを複合型プロパティにリファクタリング](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100))と[方法。作成し、複合型を変更](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))します。  
  
## <a name="example"></a>例  
 次の例のコレクションを返すクエリを実行する`Contact`オブジェクトし、の 2 つのプロパティを表示、`Contact`オブジェクト:`ContactID`との値、`EmailPhoneComplexType`複合型。  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
