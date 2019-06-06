---
title: '軽減策: カスタムの IMessageFilter.PreFilterMessage 実装'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3ac43b574c4382c4aec5070acde0fa77516727d
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251145"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>軽減策: カスタムの IMessageFilter.PreFilterMessage 実装

.NET Framework の .NET Framework 4.6.1 以降のバージョンを対象とする Windows フォーム アプリでは、<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> メソッドが呼び出されると、カスタムの <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 実装は <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 実装が次のような場合に、メッセージを安全にフィルター処理できます。

- 次の操作のいずれか、または両方を行う場合:

  - <xref:System.Windows.Forms.Application.AddMessageFilter%2A> メソッドを呼び出してメッセージ フィルターを追加する。

  - <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> メソッドを呼び出してメッセージ フィルターを削除する。 メソッドをオーバーライドします。

- **なおかつ**、<xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> メソッドを呼び出してメッセージをポンプする場合。

## <a name="impact"></a>影響

この変更によって影響を受けるのは、.NET Framework の .NET Framework 4.6.1 以降のバージョンを対象とする Windows フォーム アプリのみです。

.NET Framework の以前のバージョンを対象とする Windows フォーム アプリの場合、このような実装で、<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> メソッドが呼び出されると <xref:System.IndexOutOfRangeException> 例外がスローされることがあります。

## <a name="mitigation"></a>軽減策

この変更が望ましくない場合は、.NET Framework 4.6.1 以降のバージョンを対象とするアプリでこの変更を無効にできます。これは、そのアプリの構成ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して行います。

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

また、以前のバージョンの .NET Framework を対象とするものの、.NET Framework 4.6.1 以降のバージョンで実行されているアプリでは、そのアプリの構成ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、この動作を有効にすることができます。

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>関連項目

- [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
