---
ms.openlocfilehash: ef0381dc2ce4373b2a62e8ebefa44152059ca332
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234697"
---
### <a name="xml-schema-validation-is-stricter"></a>XML スキーマ検証がより厳格になりました

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、XML スキーマ検証が厳格化されました。 xsd:anyURI を使用して mailto プロトコルなどの URI を検証したときに、URI にスペースが入っていると検証は失敗します。 .NET Framework の以前のバージョンでは、検証は成功していました。 この変更は、.NET Framework 4.5 を対象とするアプリケーションにのみ影響します。|
|提案される解決策|より緩やかな .NET Framework 4.0 の検証が必要な場合、検証アプリケーションはバージョン 4.0 の .NET Framework をターゲットにできます。 もう一度 .NET Framework 4.5 をターゲットにする場合は、無効な URI (およびスペース) が anyURI データ型の属性値として予期されないように、コード レビューを行う必要があります。|
|スコープ|マイナー|
|Version|4.5|
|型|再ターゲット中|
