---
ms.openlocfilehash: ff4d67a1c821fc96130c4efbd88eb5c56766da06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804420"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>WPF DispatcherSynchronizationContext.CreateCopy は、現在のインスタンスの代わりに新しいコピーを返すようになった

|   |   |
|---|---|
|説明|.NET Framework 4 では、<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> は、主にパフォーマンスの最適化として、現在のインスタンスへの参照を返しました。 .NET Framework 4.5 では、これが新しいインスタンスになり、参照が等しければ、実行中のスレッドが正しい同期コンテキストにあると結論付けることが初めて可能になりました。  これらの参照の ID をチェックするコードが影響を受ける可能性は低いですが、この変更により、<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> を呼び出すコードは、.NET Framework 4.5 以降への移行の一部としてテストする必要があります。|
|提案される解決策|<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> が新しい <xref:System.Threading.SynchronizationContext?displayProperty=name> オブジェクトを返すようになったことに注意してください。 以前は、このように生成された参照の等価性を使用するコードは、実際には、正しいコンテキストにあるかどうかを確認していませんでしたが、.NET Framework 4.5 以降でのビルド時には確認を行います。  問題になる可能性は低いですが、影響を受けるコードのパスをよく調べて、何か問題が生じないかどうか確認する必要があります。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
