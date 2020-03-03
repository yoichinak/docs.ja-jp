---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235753"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>.NET Framework 4.5 でシリアル化された MailMessage オブジェクトの逆シリアル化が失敗する可能性がある

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、<xref:System.Web.Mail.MailMessage> オブジェクトに非 ASCII 文字を含めることができます。 .NET Framework 4 では、ASCII 文字しかサポートされていません。 非 ASCII 文字が含まれ、.NET Framework 4.5 以降でシリアル化された <xref:System.Web.Mail.MailMessage> オブジェクトは、.NET Framework 4 で逆シリアル化することはできません。|
|提案される解決策|<xref:System.Web.Mail.MailMessage> オブジェクトの逆シリアル化時に、コードで例外処理が提供されることを確認します。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
