---
title: インスタンス完了アクション
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 646015fbcdb7c734ae8584c7ca3979d64b81339f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791119"
---
# <a name="instance-completion-action"></a>インスタンス完了アクション
**インスタンス完了アクション**SQL Workflow Instance Store のプロパティを使用して、削除かどうか、データとワークフロー インスタンスのメタデータは永続性データベースからインスタンスの完了後を指定できます。 このプロパティの使用できる値は**DeleteAll**と**DeleteNothing**します。 これらのオプションについて次の一覧で説明します。  
  
- **DeleteAll (既定値)。** このプロパティの値を DeleteAll に設定すると、ワークフロー インスタンスの完了後に、永続性データベースからワークフロー インスタンスのデータおよびメタデータは削除されます。  
  
- **DeleteNothing します。** このプロパティの値を DeleteNothing に設定すると、ワークフロー インスタンスが完了しても、ワークフロー インスタンスのデータおよびメタデータは永続性データベースに残ります。  
  
    > [!CAUTION]
    >  インスタンスの完了後にインスタンス状態情報を残すと、永続性データベースのサイズが大きくなります。 データベースのサイズが大きくなるにつれて、永続性サブシステムが実行するデータベース操作にかかる時間が長くなります。そのため、永続性データベースからインスタンス状態情報を定期的に削除して、パフォーマンスの要件を満たすレベルでサービスが実行されるようにします。
