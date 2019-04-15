---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235526"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>ASP.Net MVC4 アプリのプロファイリングにより、致命的な実行エンジン エラーが発生する可能性がある

|   |   |
|---|---|
|説明|NGEN/プロファイル アセンブリを使用するプロファイラーにより、起動時にプロファイルされた ASP.NET MVC4 アプリケーションがクラッシュし、"致命的な実行エンジン例外" が示される場合があります。|
|提案される解決策|この問題は、.NET Framework 4.5.2 で修正されます。 プロファイラーは、イベント マスクで <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> を指定することで、この問題を回避することもできます。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
