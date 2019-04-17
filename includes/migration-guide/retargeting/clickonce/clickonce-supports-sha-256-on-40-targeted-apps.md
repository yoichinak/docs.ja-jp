---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234489"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>4.0 を対象とするアプリの ClickOnce が SHA-256 に対応

|   |   |
|---|---|
|説明|以前は、SHA-256 で署名された証明書が与えられた ClickOnce アプリには、アプリの対象が 4.0 の場合でも、.NET Framework 4.5 以降が必要でした。 それが今では、SHA-256 で署名されている場合でも、.NET Framework 4.0 を対象とする ClickOnce アプリを .NET Framework 4.0 で実行できるようになりました。|
|提案される解決策|この変更により、その依存関係がなくなったので、.NET Framework 4 以前のバージョンを対象とする ClickOnce アプリの署名に SAH-256 証明書が使用できるようになりました。|
|スコープ|マイナー|
|Version|4.6|
|型|再ターゲット中|
