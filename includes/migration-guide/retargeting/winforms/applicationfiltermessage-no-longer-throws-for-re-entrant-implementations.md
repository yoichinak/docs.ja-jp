---
ms.openlocfilehash: 8e37007318a55188d44607fd5e4c4f3950c105df
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761102"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage は、IMessageFilter.PreFilterMessage の再入可能な実装についてスローしなくなりました

|   |   |
|---|---|
|説明|.NET Framework 4.6.1 以前は、<xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> または <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (さらに <xref:System.Windows.Forms.Application.DoEvents>) を呼び出す<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> で <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> を呼び出すと、<xref:System.IndexOutOfRangeException?displayProperty=name> が発生していました。<p/>.NET Framework 4.6.1 以降を対象とするアプリケーションでは、この例外がスローされなくなり、上述の再入可能フィルターを使用できます。|
|提案される解決策|上述の再入可能な <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> の動作に対して <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> はスローされなくなります。 これは、.NET Framework 4.6.1 をターゲットとするアプリケーションにのみ影響します。 .NET Framework 4.6.1 を対象とするアプリは、[DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) 互換性スイッチを使用することによって、この変更を解除できます (または、以前の Framework をターゲットとしているアプリは、変更を受け入れることができます)。|
|スコープ|エッジ|
|Version|4.6.1|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|

