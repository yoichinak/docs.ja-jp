---
ms.openlocfilehash: a7a8bd1a9823a621f3a63c6877da9454489b48fd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858441"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>AllowCustomPaging が true に設定された GridView では、ビューの最終ページから他に移動するときに、PageIndexChanging イベントが発生する場合がある

|   |   |
|---|---|
|説明|.NET Framework 4.5 でのバグのため、<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name> が有効になっている <xref:System.Web.UI.WebControls.GridView?displayProperty=name> に対して <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> が発生しないことがあります。|
|提案される解決策|この問題は .NET Framework 4.6 で修正されたため、このバージョンの .NET Framework にアップグレードすることによって対処できます。 回避策として、アプリでは、これらの条件 (<xref:System.Web.UI.WebControls.GridView?displayProperty=name> が最終ページで、最後の <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> が <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> と異なる) を満たす <code>Page_Load</code> で明示的に BindGrid を行うことができます。 または、(カスタム ページングではなく) ページングを許可するようにアプリを変更することもできます。このシナリオでは問題は発生していません。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|

