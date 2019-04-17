---
ms.openlocfilehash: cbd599f7467c3b360bbe1c76a65abfdb840a1530
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236638"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a>WPF が wisptis.exe プロセスを生成し、マウスがフリーズする可能性がある

|   |   |
|---|---|
|説明|この問題は 4.5.2 から発生するようになり、<code>wisptis.exe</code> が生成され、マウス入力がフリーズする可能性があります。|
|提案される解決策|この問題はサービス リリースの .NET Framework 4.5.2 (修正プログラム ロールアップ 3026376) で、あるいは .NET Framework 4.6 にアップグレードすることで解決できます。|
|スコープ|Major|
|Version|4.5.2|
|型|ランタイム|
