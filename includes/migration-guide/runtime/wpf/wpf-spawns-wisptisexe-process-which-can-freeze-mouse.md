---
ms.openlocfilehash: 0d8108ef1c5b815b42003c247b4ff39099b2361a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803215"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a>WPF が wisptis.exe プロセスを生成し、マウスがフリーズする可能性がある

|   |   |
|---|---|
|説明|この問題は 4.5.2 から発生するようになり、<code>wisptis.exe</code> が生成され、マウス入力がフリーズする可能性があります。|
|提案される解決策|この問題はサービス リリースの .NET Framework 4.5.2 (修正プログラム ロールアップ 3026376) で、あるいは .NET Framework 4.6 にアップグレードすることで解決できます。|
|スコープ|Major|
|Version|4.5.2|
|型|ランタイム|

