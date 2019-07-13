---
ms.openlocfilehash: 47d0aa554d88726caca35fa6bebe4d863fdc0695
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804424"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource.WriteEvent impls は、受け取ったのと同じパラメーター (と ID) を WriteEvent に渡す必要がある

|   |   |
|---|---|
|説明|ランタイムは次の内容を指定するコントラクトを強制するようになりました。ETW イベント メソッドを定義する <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> から派生するクラスは、ETW イベント メソッドが渡された同じ引数が続くイベント ID の基底クラス <code>EventSource.WriteEvent</code> メソッドを呼び出す必要があります。|
|提案される解決策|<xref:System.IndexOutOfRangeException?displayProperty=name> 例外は、<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> がこのコントラクトに違反するイベント ソースのプロセスの <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> データを読み取るときに、スローされます。|
|スコープ|マイナー|
|Version|4.5.1|
|型|ランタイム|
