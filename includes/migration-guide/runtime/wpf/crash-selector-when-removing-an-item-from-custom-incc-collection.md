---
ms.openlocfilehash: a573a78109036b87201b53f72aa8dba6755e7a21
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804382"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>カスタム INCC コレクションから項目を削除すると、セレクターでクラッシュが発生する

|   |   |
|---|---|
|説明|<code>T:System.InvalidOperationException</code> は、次のシナリオで発生する可能性があります。<ul><li><code>T:System.Windows.Controls.Primitives.Selector</code> の ItemsSource が、<code>T:System.Collections.Specialized.INotifyCollectionChanged</code> のカスタム実装を含むコレクションである。</li><li>選択した項目をコレクションから削除する。</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> の <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> が -1 (不明な位置を示す) である。</li></ul>例外のコールスタックは、System.Windows.Threading.Dispatcher.VerifyAccess()、System.Windows.DependencyObject.GetValue(DependencyProperty dp)、System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element) で始まります。アプリケーションに複数のディスパッチャー スレッドがある場合、この例外は .NET Framework 4.5 で発生する可能性があります。 .NET Framework 4.7 では、1 つのディスパッチャー スレッドのアプリケーションでも例外が発生する場合があります。 この問題は .NET Framework 4.7.1 で修正されます。|
|提案される解決策|.NET Framework 4.7.1 にアップグレードします。|
|スコープ|マイナー|
|Version|4.7|
|型|ランタイム|
