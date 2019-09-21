---
title: ワークフローの探索のサンプル
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 56437607d6e940b59698641ad3305c525d8f7095
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045394"
---
# <a name="workflow-discovery-sample"></a>ワークフローの探索のサンプル
このサンプルでは、ワークフロー サービスを探索可能にする方法と、特定のサービスを検索するカスタム コード アクティビティを作成する方法を示します。  
  
## <a name="demonstrates"></a>使用例  
 探索検索アクティビティとワークフローの使用方法  
  
## <a name="discussion"></a>説明  
 サンプルの最初の部分では、構成を使用してワークフロー サービスを探索可能にしています。 また、カスタム メタデータ (スコープなど) と共に構成を使用すると、サービスを適切に適用することができます。 このサンプルは、クライアントでカスタム コード アクティビティを使用します。カスタム コード アクティビティは、探索を使用して、特定のコントラクトに一致するサービスを検索します。 コード アクティビティは URI を出力します。この URI は、後で送信アクティビティで使用されます。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. このサンプルでは、適切な URL Acl を実行する必要がある HTTP エンドポイントを使用します (詳細については、「 [http および HTTPS の構成](https://go.microsoft.com/fwlink/?LinkId=70353)」を参照してください)。 権限のレベルが高いコマンド プロンプトで次のコマンドを実行すると、適切な ACL が追加されます。 使用中のシェルで変数の形式を使用できない場合は、代わりに、ドメインとユーザー名を引数に指定してください。  
  
     **netsh http add urlacl url =http://+:8000/ user =% DOMAIN%\\ % UserName%**  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
