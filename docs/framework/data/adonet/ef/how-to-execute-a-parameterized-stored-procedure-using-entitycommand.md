---
title: '方法: EntityCommand を使用してパラメーター化されたストアド プロシージャを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: deb1877397053ceab8c284a537a861ba56ffb729
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326659"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>方法: EntityCommand を使用してパラメーター化されたストアド プロシージャを実行する
このトピックでは、<xref:System.Data.EntityClient.EntityCommand> クラスを使用して、パラメーター化されたストアド プロシージャを実行する方法を示します。  
  
### <a name="to-run-the-code-in-this-example"></a>この例のコードを実行するには  
  
1. 追加、 [School モデル](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))をプロジェクトに使用するプロジェクトを構成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]します。 詳細については、「[方法 :エンティティ データ モデル ウィザードを使用して](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))します。  
  
2. アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. `GetStudentGrades` ストアド プロシージャをインポートし、戻り値の型として `CourseGrade` エンティティを指定します。 ストアド プロシージャをインポートする方法については、次を参照してください。[方法。ストアド プロシージャをインポート](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100))します。  
  
## <a name="example"></a>例  
 次のコードでは、`GetStudentGrades` ストアド プロシージャが実行されます。`StudentId` は必須パラメーターです。 結果は <xref:System.Data.EntityClient.EntityDataReader> によって読み取られます。  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>関連項目

- [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
