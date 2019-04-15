---
ms.openlocfilehash: c9d6111edcfeec6852f23cc0768833de32e61022
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235550"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>maxRequestLength または maxReceivedMessageSize のエラー コードが異なる

|   |   |
|---|---|
|説明|Internet Information Services (IIS) または ASP.NET 開発サーバーでホストされており、maxRequestLength (ASP.NET の場合) または maxReceivedMessageSize (WCF の場合) を超える WCF Web サービスのメッセージに異なるエラー コードがあります。HTTP 状態コードは 400 (正しくない要求) から 413 (要求したエンティティが大きすぎます) に変更され、maxRequestLength または maxReceivedMessageSize 設定を超えるメッセージでは <xref:System.ServiceModel.ProtocolException?displayProperty=name> 例外がスローされます。 これには、転送モードが Streamed である場合も含まれます。|
|提案される解決策|この変更により、メッセージ長が ASP.NET または WCF で許可されている制限を超えたときのデバッグが簡単になります。HTTP 400 状態コードに基づいて処理を実行するコードはすべて変更する必要があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
