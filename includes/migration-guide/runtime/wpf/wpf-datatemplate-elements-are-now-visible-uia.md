---
ms.openlocfilehash: 51691ced3f05201f784ccdeffbc130e34748b7c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379703"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>WPF DataTemplate 要素が UIA に表示されるようになった

|   |   |
|---|---|
|説明|以前は、<xref:System.Windows.DataTemplate?displayProperty=name> 要素は UI オートメーションには表示されませんでした。 4.5 から、UI オートメーションは、これらの要素を検出します。 これは、多くの場合に便利ですが、<xref:System.Windows.DataTemplate?displayProperty=name> 要素を含まない UIA ツリーに依存するテストは中断することがあります。|
|提案される解決策|このアプリの UI オートメーション テストを更新して、以前は非表示の <xref:System.Windows.DataTemplate?displayProperty=name> 要素を含んでいる UIA ツリーに対応できるようにしなければならないことがあります。 たとえば、いくつかの要素が互いに隣り合っていることを予期しているテストでは、以前は非表示であった UIA 要素が間にあることを予期する必要があります。 または、UIA 要素の特定のカウントまたはインデックスに依存するテストは、新しい値で更新しなければならないことがあります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|
