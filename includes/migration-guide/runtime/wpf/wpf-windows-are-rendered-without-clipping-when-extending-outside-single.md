---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234196"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>1 つのモニターの外部に拡張すると、クリッピングなしで WPF ウィンドウがレンダリングされる

|   |   |
|---|---|
|説明|Windows 8 以上で実行している .NET Framework 4.6 では、マルチ モニターのシナリオで 1 つのディスプレイの外部にウィンドウを拡張すると、ウィンドウ全体がクリッピングなしでレンダリングされます。 これは、1 つのディスプレイを超える WPF ウィンドウをクリッピングする、以前のバージョンの .NET Framework とは異なります。|
|提案される解決策|この動作 (クリッピングするかどうか) は、アプリケーションの構成ファイルの <code>&lt;appSettings&gt;</code> で <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> 要素を使用するか、アプリの起動時に <code>EnableMultiMonitorDisplayClipping</code> プロパティを設定することで明示的に設定できます。|
|スコープ|マイナー|
|Version|4.6|
|型|ランタイム|
