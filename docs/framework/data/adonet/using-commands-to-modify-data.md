---
title: コマンドを使用したデータ変更
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: f2e3d162bfbdcb79cfecefa4ddc8e6a0dc46ee3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102454"
---
# <a name="using-commands-to-modify-data"></a>コマンドを使用したデータ変更
.NET Framework データ プロバイダーを使用すると、ストアド プロシージャまたはデータ定義言語のステートメント (たとえば、CREATE TABLE、ALTER COLUMN など) を実行して、データベースやカタログに対するスキーマ操作を実行できます。 クエリとは、これらのコマンドは行を返しませんため、**コマンド**オブジェクトは、提供、 **ExecuteNonQuery**それらを処理します。  
  
 使用するだけでなく**ExecuteNonQuery**スキーマを変更するには、データを変更するが、INSERT、UPDATE などの行を返すなく、削除のプロセスの SQL ステートメントには、このメソッドも使用できます。  
  
 行は返されませんが、 **ExecuteNonQuery**メソッド、入力と出力パラメーターと戻り値を渡すし、を介して返されます、**パラメーター**のコレクション、**コマンド**オブジェクト。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データ ソースのデータの更新](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 データベース内のデータを変更するコマンドまたはストアド プロシージャを実行する方法について説明します。  
  
 [カタログ操作の実行](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 データベース スキーマを変更するコマンドを実行する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [コマンドおよびパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
