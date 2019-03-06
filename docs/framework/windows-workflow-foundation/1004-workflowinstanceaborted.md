---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485188"
---
# <a name="1004---workflowinstanceaborted"></a>1004 - WorkflowInstanceAborted

## <a name="properties"></a>プロパティ

|||
|-|-|
|ID|1004|
|キーワード|WFRuntime|
|レベル|情報|
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|

## <a name="description"></a>説明

例外で、ワークフロー インスタンスが中止を示します。

## <a name="message"></a>メッセージ

WorkflowInstance ID: '%1' は例外により中止されました。

## <a name="details"></a>詳細

|データ項目名|データ項目の型|説明|
|--------------------|--------------------|-----------------|
|WorkflowInstanceId|`xs:string`|ワークフローのインスタンス ID|
|例外|`xs:string`|例外の詳細|
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
