---
ms.openlocfilehash: e2bca42daebd25667ab2f312d5e59089b986503c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774452"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>AntiXSSEncoder を使用するときの複数行の ASP.Net TextBox の間隔が変更

|   |   |
|---|---|
|説明|.NET Framework 4.0 では、<xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name> を使用する場合、ポストバックの複数行テキスト ボックスの行間に余分な行が挿入されました。 .NET Framework 4.5 では、これらの余分な改行は含まれませんが、web アプリが .NET Framework 4.5 を対象としている場合に限ります。|
|提案される解決策|4.0 の Web アプリの対象を .NET Framework 4.5 に変更すると、複数行テキスト ボックスが改善され、余分な改行が挿入されなくなります。 これが望ましくない場合は、.NET Framework 4.0 を対象とすることによって、アプリを .NET Framework 4.5 で実行するときにも以前の動作が可能です。|
|スコープ|マイナー|
|Version|4.5|
|型|再ターゲット中|
