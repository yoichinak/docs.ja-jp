---
title: 'コア通信: 接続フレームワーク'
ms.date: 03/30/2017
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
ms.openlocfilehash: a3f52ac82c2bf09ded504e412d7f216dd0b39959
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998687"
---
# <a name="core-communications-connection-framework"></a>コア通信: 接続フレームワーク
このトピックでは、Windows Communication Foundation (WCF) 接続フレームワークによって生成されるすべての例外を使用します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|CloseTimedOut|Close メソッドは、指定された時間の経過後にタイムアウトしました。 Close の呼び出しに渡されるタイムアウト値を増やすか、バインディングの CloseTimeout 値を増やします。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|  
|ContentTypeMismatch|指定されたものを予期していたサービスに対して、指定されたコンテンツ タイプが送信されました。 クライアントとサービスのバインディングは一致しない場合もあります。|  
|DuplexChannelAbortedDuringOpen|指定対象への二重チャネルは、開始処理中に中止されました。|  
|FramingValueNotAvailable|完全にデコードされていないため、値にアクセスできません。|  
|OperationAbortedDuringConnectionEstablishment|指定対象への接続の確立中に操作が中止されました。|  
|ReceiveTimedOut2|受信操作は指定された時間の経過後にタイムアウトになります。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|  
|SendCannotBeCalledAfterCloseOutputSession|CloseOutputSession の呼び出し後にチャネルでメッセージを送信することはできません。|
