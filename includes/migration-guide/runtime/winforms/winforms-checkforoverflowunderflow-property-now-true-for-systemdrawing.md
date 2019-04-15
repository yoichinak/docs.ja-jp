---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235562"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>WinForm の CheckForOverflowUnderflow プロパティが System.Drawing に対して true に設定されるようになった

|   |   |
|---|---|
|説明|System.Drawing.dll アセンブリの CheckForOverflowUnderflow プロパティが true に設定されます。|
|提案される解決策|これまではオーバーフローが発生すると、その結果は自動的に切り捨てられました。 現在では、<xref:System.OverflowException?displayProperty=name> 例外がスローされます。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
