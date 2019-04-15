---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236655"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC は、ルート パラメーターで渡された文字列内のスペースをエスケープするようになりました

|   |   |
|---|---|
|説明|RFC 2396 に準拠するために、ルートからアクション パラメーターを設定するときに、ルートのパスに含まれるスペースがエスケープされるようになりました。 そのため、<code>/controller/action/some data</code> は以前はルート <code>/controller/action/{data}</code> し、<code>some data</code> をデータ パラメーターとして与えましたが、代わりに <code>some%20data</code> を与えるようになります。|
|提案される解決策|ルートからの文字列パラメーターをエスケープ解除するように、コードを更新する必要があります。 元の URI が必要な場合は、<xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API でアクセスできます。|
|スコープ|マイナー|
|Version|4.5.2|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
