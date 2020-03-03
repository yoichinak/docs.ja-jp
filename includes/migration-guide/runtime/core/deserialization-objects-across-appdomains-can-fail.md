---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804373"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>アプリ ドメイン全体でのオブジェクトの逆シリアル化に失敗する可能性がある

|   |   |
|---|---|
|説明|場合によっては、アプリが異なるアプリケーション ベースを持つ複数のアプリ ドメインを使用すると、アプリ ドメイン間で論理呼び出しコンテキストのオブジェクトを逆シリアル化しようとして、例外がスローされます。|
|提案される解決策|「[軽減策:アプリ ドメイン全体でのオブジェクトの逆シリアル化](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)」を参照してください。|
|スコープ|エッジ|
|Version|4.5.1|
|型|ランタイム|
