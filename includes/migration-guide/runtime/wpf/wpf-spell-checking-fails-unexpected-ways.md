---
ms.openlocfilehash: 8049bf01bc10c5913fa11b25e49afd1b1317eecc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802965"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>WPF スペル チェックが予期しない方法で失敗する

|   |   |
|---|---|
|説明|これには、次の WPF スペル チェックのいくつかの問題が含まれます。<ul><li>WPF スペル チェックで <xref:System.Runtime.InteropServices.COMException?displayProperty=name> がスローされる場合がある。</li><li>"別のユーザーとして実行" を使用してアプリケーションが起動された場合、WPF スペル チェックが <xref:System.UnauthorizedAccessException> で失敗する。</li><li>WPF スペル チェックで、ドイツ語の "Hausnummer" などの複合語のスペル ミスが正しく識別されない。</li></ul>|
|提案される解決策|問題 1 - これは .NET Framework 4.6.2 で修正されました。問題 2 - "別のユーザーとして実行" を使用してアプリケーションが起動された場合、WPF スペル チェックがサポートされなくなりました。 .NET Framework 4.6.2 以降では、このように起動されたアプリケーションが予期せずクラッシュしなくなります。代わりに、スペル チェックが自動的に無効になります。 問題 3 - これは .NET Framework 4.6.2 で修正されました。|
|スコープ|エッジ|
|Version|4.6.1|
|型|ランタイム|

