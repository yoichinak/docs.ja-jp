---
title: セキュリティ
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: f47b75fa1fd345869f560326861ebc31e6b5e1a9
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045313"
---
# <a name="security"></a>セキュリティ
SQL Workflow Instance Store は、次のデータベース セキュリティ ロールを使用して、永続性データベースのインスタンス状態情報へのアクセスをセキュリティ保護します。  
  
- **System.activities.durableinstancing.instances を処理**します。 このロールには、パブリック ビューへの読み取りおよび書き込みのアクセス権と、インスタンスの作成、読み込み、保存に関連するストアド プロシージャへの実行権限があります。  
  
- **System.activities.durableinstancing.instances. InstanceStoreObservers**。 このロールには、パブリック ビューへの読み取り専用アクセス権があります。  
  
- **System.activities.durableinstancing.instances. WorkflowActivationUsers**. このロールには、インスタンスのアクティベーション プロセスにかかわるストアド プロシージャへの実行権限があります。 インスタンスのアクティブ化の詳細については、「[インスタンスのアクティブ化](instance-activation.md)」を参照してください。 汎用ホスト (Windows Server AppFabric のホスト機能のワークフロー管理サービスなど) を実行するユーザーアカウントは、このデータベースロールに追加する必要があります。  
  
 Windows Server App Fabric での永続化ストアのセキュリティの詳細については、「 [App fabric の永続ストアのセキュリティ構成](https://go.microsoft.com/fwlink/?LinkId=201208)」を参照してください。  
  
> [!CAUTION]
> インスタンス ストア内にある固有のインスタンス データへのアクセス権を持つクライアントは、同じインスタンス ストア内にあるその他すべてのインスタンスにもアクセスできます。 インスタンス ストアでは、インスタンス レベルでセキュリティ アクセス許可を指定することはできません。 個別のインスタンス ストアを作成し、ストアごとに、各グループやユーザーのアクセス権を設定します。
