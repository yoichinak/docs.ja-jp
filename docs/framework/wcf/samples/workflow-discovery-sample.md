---
title: ワークフローの探索のサンプル
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b3a2d88028f3854746d4e1d2fad80aae4f6be7be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143487"
---
# <a name="workflow-discovery-sample"></a>ワークフローの探索のサンプル
このサンプルでは、ワークフロー サービスを探索可能にする方法と、特定のサービスを検索するカスタム コード アクティビティを作成する方法を示します。  
  
## <a name="demonstrates"></a>対象  
 探索検索アクティビティとワークフローの使用方法  
  
## <a name="discussion"></a>ディスカッション  
 サンプルの最初の部分では、構成を使用してワークフロー サービスを探索可能にしています。 また、カスタム メタデータ (スコープなど) と共に構成を使用すると、サービスを適切に適用することができます。 このサンプルは、クライアントでカスタム コード アクティビティを使用します。カスタム コード アクティビティは、探索を使用して、特定のコントラクトに一致するサービスを検索します。 コード アクティビティは URI を出力します。この URI は、後で送信アクティビティで使用されます。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. このサンプルでは、実行する適切な URL ACL が必要な HTTP エンドポイントを使用します (詳細については[、HTTP と HTTPS の構成を](../feature-details/configuring-http-and-https.md)参照してください)。 権限のレベルが高いコマンド プロンプトで次のコマンドを実行すると、適切な ACL が追加されます。 シェルで変数の形式がわからない場合は、次の引数をドメインとユーザー名に置き換えてください。  
  
     **ネットッシュ http 追加 urlacl url=http://+:8000/ \\ユーザー =%ドメイン% %ユーザー名%**  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
