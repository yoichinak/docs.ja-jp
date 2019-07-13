---
title: セキュリティ
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: cbfb82c2db329725d3445e1a88b54e01d5813f36
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348398"
---
# <a name="security"></a>セキュリティ
SQL Workflow Instance Store は、次のデータベース セキュリティ ロールを使用して、永続性データベースのインスタンス状態情報へのアクセスをセキュリティ保護します。  
  
- **System.Activities.DurableInstancing.InstanceStoreUsers**します。 このロールには、パブリック ビューへの読み取りおよび書き込みのアクセス権と、インスタンスの作成、読み込み、保存に関連するストアド プロシージャへの実行権限があります。  
  
- **System.Activities.DurableInstancing.InstanceStoreObservers**します。 このロールには、パブリック ビューへの読み取り専用アクセス権があります。  
  
- **System.Activities.DurableInstancing.WorkflowActivationUsers**します。 このロールには、インスタンスのアクティベーション プロセスにかかわるストアド プロシージャへの実行権限があります。 インスタンスのアクティブ化の詳細については、次を参照してください。[インスタンスのアクティベーション](instance-activation.md)します。 (Windows Server AppFabric のホスティング機能のワークフロー管理サービス) などの汎用ホストを実行するユーザー アカウントは、このデータベース ロールに追加する必要があります。  
  
 Windows Server App Fabric で永続化ストアのセキュリティの詳細については、次を参照してください[App Fabric の永続化ストアのセキュリティの構成。](https://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  インスタンス ストア内にある固有のインスタンス データへのアクセス権を持つクライアントは、同じインスタンス ストア内にあるその他すべてのインスタンスにもアクセスできます。 インスタンス ストアでは、インスタンス レベルでセキュリティ アクセス許可を指定することはできません。 個別のインスタンス ストアを作成し、ストアごとに、各グループやユーザーのアクセス権を設定します。
