---
title: '方法: WCF サービス操作を非同期的に呼び出す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 19b09c9ec789419f2774207b051b8ee488b6725d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625550"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>方法: WCF サービス操作を非同期的に呼び出す
ここでは、クライアントからサービス操作に非同期にアクセスする方法について説明します。 このトピックのサービスは、`ICalculator` インターフェイスを実装しています。 クライアントは、イベント ドリブンの非同期呼び出しモデルを使用して、このインターフェイスで操作を非同期に呼び出すことができます  (イベント ベースの非同期呼び出しモデルの詳細については、次を参照してください。[イベント ベースの非同期パターンを使用したマルチ スレッド プログラミング](https://go.microsoft.com/fwlink/?LinkId=248184))。 サービスで操作を非同期的に実装する方法の例を参照してください[方法。非同期サービス操作を実装](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)します。 同期および非同期操作の詳細については、[同期および非同期操作](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)を参照してください。  
  
> [!NOTE]
>  <xref:System.ServiceModel.ChannelFactory%601> を使用している場合、イベント ドリブンの非同期呼び出しモデルはサポートされません。 使用して非同期呼び出しを行う方法については、<xref:System.ServiceModel.ChannelFactory%601>を参照してください[方法。チャネル ファクトリを使用して非同期的に操作を呼び出す](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)します。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>WCF サービス操作を非同期に呼び出すには  
  
1.  実行、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)両方のツール、`/async`と`/tcv:Version35`次のコマンドで示すように、このコマンド オプションをまとめてします。  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     これは、クラスを生成、だけでなく、同期操作と標準的なデリゲートに基づく非同期操作、WCF クライアントが含まれています。  
  
    -   2 つ <`operationName` > `Async` -イベント ベースの非同期呼び出し方法で使用するための操作。 例:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   フォームの操作完了イベント <`operationName` > `Completed` -イベント ベースの非同期呼び出し方法を使用します。 例:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType> 各操作の種類 (形式の <`operationName`>`CompletedEventArgs`) - イベント ベースの非同期呼び出し方法を使用します。 例:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  次のサンプル コードに示すように、呼び出し元アプリケーションで、非同期操作の完了時に呼び出されるコールバック メソッドを作成します。  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  操作を呼び出す前に、新しいジェネリックを使用して<xref:System.EventHandler%601?displayProperty=nameWithType>型の <`operationName` > `EventArgs` (前の手順で作成した) ハンドラー メソッドを追加して、<`operationName` > `Completed`イベント。 まず、<`operationName` > `Async`メソッド。 例:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>例  
  
> [!NOTE]
>  イベント ベースの非同期モデルのデザイン ガイドラインには、複数の値を返す場合に、1 つの値を `Result` プロパティとして返し、残りの値を <xref:System.EventArgs> オブジェクトのプロパティとして返すことが記載されています。 この 1 つの結果として、クライアントがイベント ベースの非同期コマンド オプションを使用してメタデータをインポートし、操作から複数の値が返される場合、既定の <xref:System.EventArgs> オブジェクトが 1 つの値を `Result` プロパティとして返し、残りの値は <xref:System.EventArgs> オブジェクトのプロパティになります。メッセージ オブジェクトを `Result` プロパティとして受け取り、返された値をそのオブジェクトのプロパティとして取得する場合は、`/messageContract` コマンド オプションを使用します。 これにより、`Result` オブジェクトの <xref:System.EventArgs> プロパティとして応答メッセージを返すシグネチャが生成されます。 すべての内部戻り値は、応答メッセージ オブジェクトのプロパティになります。  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>関連項目
- [方法: 非同期サービス操作を実装します。](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
