---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235427"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>HttpRequest.ContentEncoding プロパティで UTF7 が禁止される

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、<xref:System.Web.HttpRequest?displayProperty=name> の本文では UTF-7 エンコードが禁止されます。 UTF-7 データの受信を必要とするアプリケーションのデータが、正しくデコードされない場合があります。|
|提案される解決策|理想的には、<xref:System.Web.HttpRequest?displayProperty=name> で UTF-7 エンコードを使用しないようにアプリケーションを更新する必要があります。 または、 [<appSettings>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) 要素の <code>aspnet:AllowUtf7RequestContentEncoding</code> 属性を使用して、レガシ動作に戻すことができます。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
