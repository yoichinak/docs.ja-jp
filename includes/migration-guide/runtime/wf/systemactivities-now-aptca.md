---
ms.openlocfilehash: 6cc1c65a95238e758f99090794f5e50b830d9667
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804355"
---
### <a name="systemactivities-is-now-aptca"></a>System.Activities が APTCA に

|   |   |
|---|---|
|説明|アセンブリは <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=name> 属性でマークされています。|
|提案される解決策|派生クラスに <xref:System.Security.SecurityCriticalAttribute?displayProperty=name>のマークを付けることはできません。 以前は、派生型に <xref:System.Security.SecurityCriticalAttribute?displayProperty=name>マークを付ける必要がありました。 ただし、この変更によって生じる実質的な影響はないはずです。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
