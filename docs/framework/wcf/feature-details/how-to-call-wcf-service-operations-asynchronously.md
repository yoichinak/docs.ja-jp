---
title: '方法: WCF サービス操作を非同期に呼び出す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 2d075bfebf7b5cbd2b2ce031a1c3855a925405a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964026"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>方法: WCF サービス操作を非同期に呼び出す
ここでは、クライアントからサービス操作に非同期にアクセスする方法について説明します。 このトピックのサービスは、`ICalculator` インターフェイスを実装しています。 クライアントは、イベント ドリブンの非同期呼び出しモデルを使用して、このインターフェイスで操作を非同期に呼び出すことができます (イベントベースの非同期呼び出しモデルの詳細については、「[イベントベースの非同期パターンを使用したマルチスレッドプログラミング](https://go.microsoft.com/fwlink/?LinkId=248184)」を参照してください)。 サービスで操作を非同期に実装する方法を示す例については[、「方法:非同期サービス操作](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)を実装します。 同期操作と非同期操作の詳細については、「[同期操作と非同期操作](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)」を参照してください。  
  
> [!NOTE]
> <xref:System.ServiceModel.ChannelFactory%601> を使用している場合、イベント ドリブンの非同期呼び出しモデルはサポートされません。 を使用した<xref:System.ServiceModel.ChannelFactory%601>非同期呼び出しの作成の詳細については、「 [方法:チャネルファクトリ](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)を使用して操作を非同期に呼び出します。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>WCF サービス操作を非同期に呼び出すには  
  
1. 次のコマンドに示すように、 `/async`との`/tcv:Version35`両方のコマンドオプションを一緒に使用して、 [ServiceModel メタデータユーティリティツール (svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールを実行します。  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     これにより、同期および標準のデリゲートベースの非同期操作に加えて、次のものを含む WCF クライアントクラスが生成されます。  
  
    - イベントベース`operationName`の非同期呼び出し方法で使用する2つの <> `Async`操作。 例:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - イベントベースの非同期呼び出し方法で`operationName`使用するために <> `Completed`フォームの操作完了イベント。 例:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType>イベントベースの非同期呼び出し方法で使用する`operationName`各操作 (フォーム <>`CompletedEventArgs`) の型。 例:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. 次のサンプル コードに示すように、呼び出し元アプリケーションで、非同期操作の完了時に呼び出されるコールバック メソッドを作成します。  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. 操作を呼び出す<xref:System.EventHandler%601?displayProperty=nameWithType>前に、<`operationName` > `EventArgs`型の新しいジェネリックを使用して、(前の手順で作成した) ハンドラーメソッドを`operationName` <> `Completed`イベントに追加します。 次に、<`operationName` > `Async`メソッドを呼び出します。 例:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>例  
  
> [!NOTE]
> イベント ベースの非同期モデルのデザイン ガイドラインには、複数の値を返す場合に、1 つの値を `Result` プロパティとして返し、残りの値を <xref:System.EventArgs> オブジェクトのプロパティとして返すことが記載されています。 この 1 つの結果として、クライアントがイベント ベースの非同期コマンド オプションを使用してメタデータをインポートし、操作から複数の値が返される場合、既定の <xref:System.EventArgs> オブジェクトが 1 つの値を `Result` プロパティとして返し、残りの値は <xref:System.EventArgs> オブジェクトのプロパティになります。メッセージ オブジェクトを `Result` プロパティとして受け取り、返された値をそのオブジェクトのプロパティとして取得する場合は、`/messageContract` コマンド オプションを使用します。 これにより、`Result` オブジェクトの <xref:System.EventArgs> プロパティとして応答メッセージを返すシグネチャが生成されます。 すべての内部戻り値は、応答メッセージ オブジェクトのプロパティになります。  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [方法: 非同期サービス操作を実装する](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
