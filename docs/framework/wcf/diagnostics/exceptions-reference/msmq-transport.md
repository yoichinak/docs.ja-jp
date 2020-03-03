---
title: MSMQ トランスポート
ms.date: 03/30/2017
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
ms.openlocfilehash: a2e5384808b82f48bd1d4856bf893130da8c5f1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959420"
---
# <a name="msmq-transport"></a>MSMQ トランスポート
ここでは、MSMQ トランスポートによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|メッセージのバインディングを検証できませんでした。 クライアントはメッセージを送信できません。 バインディングのプロパティの競合が原因でこのエラーが発生しました。 UseActiveDirectory は true に設定されており、QueueTransferProtocol は Native に設定されています。 競合を解決するには、どちらかのプロパティを適切な値に変更してください。|  
|MsmqAuthNoneRequiresProtectionNone|サービスのバインディングを検証できませんでした。 サービスのエンドポイントまたはクライアントを開始できません。 バインディングのプロパティの競合が原因でこのエラーが発生しました。 MsmqAuthenticationMode が None に設定されている場合、MsmqProtectionLevel を None に設定する必要があります。 競合を解決するには、どちらかのプロパティを適切な値に変更してください。|  
|MsmqCustomRequiresPerAddDLQ|メッセージのバインディングを検証できませんでした。 クライアントはメッセージを送信できません。 DeadLetterQueue は Custom に設定されていますが、CustomDeadLetterQueue が指定されていません。 CustomDeadLetterQueue プロパティで、各アプリケーションの配信不能メッセージ キューの URI を指定してください。|  
|MsmqDeserializationError|XML メッセージの逆シリアル化時にエラーが発生しました。 メッセージを受信できないため、破棄しました。|  
|MsmqDLQNotWriteable|クライアントのバインディングを検証できませんでした。 クライアントはメッセージを送信できません。 指定された配信不能メッセージ キューが存在していないか書き込み不能です。 このキューが存在しており、このキューに書き込むための適切な権限が割り当てられいることを確認してください。|  
|MsmqGetPrivateComputerInformationError|バージョン チェックが、指定されたエラーで失敗しました。 MSMQ のバージョンを検出できません。キューにあるチャネルでのすべての操作は失敗します。 MSMQ がインストールされており、使用可能であることを確認してください。|  
|MsmqNoAssurancesForVolatile|サービスのバインディングを検証できませんでした。 サービスのエンドポイントまたはクライアントを開始できません。 ExactlyOnce プロパティは true に設定されており、Durable プロパティは false に設定されていますが、 これはサポートされていません。 競合を解決するには、どちらかのプロパティを適切な値に変更してください。|  
|MsmqNonTransactionalQueueNeeded|バインドと MSMQ キューの構成間で不整合が検出されました。 サービス エンドポイントを開始できません。 ExactlyOnce プロパティは false に設定されており、メッセージが読み取られるキューはトランザクション キューです。 このエラーを修正するには、ExactlyOnce プロパティを true に設定するか、非トランザクション バインドを作成してください。|  
|MsmqOpenError|指定されたキュー を開く際にエラーが発生しました。 キューからメッセージを送受信できません。 MSMQ がインストールされて実行されていることを確認してください。 また、要求されたアクセス モードおよび認証を使用してキューを開いて利用できることも確認してください。|  
|MsmqPathLookupError|指定されたキュー パス名を指定の形式名に変換中にエラーが発生しました。 キュー内のチャネルに対するすべての操作が失敗しました。 キュー アドレスが有効であることを確認してください。 Active Directory 統合が有効になった状態で MSMQ がインストールされている必要があり、MSMQ にアクセスできる必要があります。|  
|MsmqPerAppDLQRequiresCustom|クライアントのバインドの検証が失敗しました。 クライアントはメッセージを送信できません。 CustomDeadLetterQueue プロパティが設定されていますが、DeadLetterQueue プロパティが Custom に設定されていません。 DeadLetterQueue プロパティを Custom に設定してください。|  
|MsmqPerAppDLQRequiresExactlyOnce|クライアントのバインディングを検証できませんでした。 クライアントはメッセージを送信できません。 バインド プロパティ内の競合が原因です。 カスタムの配信不能メッセージ キューを使用するには、ExactlyOnce を true に設定して競合を解決する必要があります。|  
|MsmqPerAppDLQRequiresMsmq4|バインドと MSMQ の構成間で不整合が検出されました。 クライアントはメッセージを送信できません。 カスタムの配信不能メッセージ キューを使用するには、MSMQ Version 4.0 以降が必要です。 MSMQ Version 4.0 以降がない場合は、DeadLetterQueue プロパティを System または None に設定してください。|  
|MsmqReceiveError|キューからのメッセージを受信中にエラーが発生しました。 MSMQ がインストールされて実行されていることを確認してください。 また、このキューからの受信が可能であることを確認してください。|  
|MsmqSameTransactionExpected|このセッションでトランザクション エラーが発生しました。 セッション チャネルは途中終了されました。 このセッション内のメッセージは送信も受信もできません。 キュー内の 1 つのセッションを複数のトランザクションに関連付けることはできません。 セッション内のすべてのメッセージが単一のトランザクションを使用して送信または受信されていることを確認してください。|  
|MsmqSendError|指定されたキューへの送信中にエラーが発生しました。 MSMQ がインストールされて実行されていることを確認してください。 ローカル キューに送信している場合は、このキューが存在しており、必要なアクセス モードと権限が設定されていることを確認してください。|  
|MsmqTimeSpanTooLarge|メッセージの Time to Live (TTL) が長すぎます。 メッセージを送信できません。 メッセージの Time To Live は Int32 の最大値を超えることはできません。|  
|MsmqTokenProviderNeededForCertificates|X509SecurityTokenProvider が見つかりません。 メッセージを送信できません。 証明書認証モードには、X.509 トークン プロバイダーが必要です。 インストールされた証明書でセキュリティ トークン プロバイダーが使用できることを確認します。|  
|MsmqTransactedDLQExpected|バインドと MSMQ の構成間で不整合が発生しました。 メッセージを送信できません。 バインドで指定されたカスタムの配信不能メッセージ キューは、トランザクション キューである必要があります。 カスタムの配信不能メッセージ キューのアドレスが正しいこと、およびこのキューがトランザクション キューであることを確認してください。|  
|MsmqTransactionalQueueNeeded|バインドと MSMQ キューの構成間で不整合が発生しました。 サービス エンドポイントを開始できません。 ExactlyOnce プロパティは true に設定されており、メッセージが読み取られるキューはトランザクション キューではありません。 このエラーを修正するには、ExactlyOnce プロパティを false に設定するか、このバインディング用のトランザクション キューを作成してください。|  
|MsmqTransactionCurrentRequired|セッションでメッセージを送信するためにトランザクションを使用できません。 キュー内のセッションにあるメッセージを送信するにはトランザクションが必要です。 セッションでメッセージを送信するためにトランザクション範囲が指定されていることを確認してください。|  
|MsmqTransactionRequired|トランザクションが必要ですが、使用できません。 メッセージが送信または受信できません。 メッセージを送信または受信するためのトランザクション範囲が指定されていることを確認してください。|  
|MsmqUnsupportedSerializationFormat|逆シリアル化エラーが発生しました。 メッセージを受信できないため、破棄しました。 指定されたシリアル化形式はサポートされていません。|  
|MsmqWrongPrivateQueueSyntax|URL が無効です。 キューの URL に '$' 文字を使用することはできません。 net.msmq://machine/private/queueName の構文を使用して、プライベート キューをアドレス指定してください。|
