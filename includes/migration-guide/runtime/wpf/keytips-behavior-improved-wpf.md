---
ms.openlocfilehash: 946096cb9510ca12bbd2cecd00099142308b072a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236131"
---
### <a name="keytips-behavior-improved-in-wpf"></a>WPF での KeyTip の動作が改良された

|   |   |
|---|---|
|説明|KeyTip の動作が、Microsoft Word やエクスプローラーでの動作と同等に変更されています。 <xref:System.Windows.Input.KeyEventArgs.SystemKey> (具体的には <xref:System.Windows.Input.Key> または <xref:System.Windows.Input.Key.F11>) が押された場合に KeyTip の状態が有効かどうかを調べることによって、WPF は KeyTip キーを適切に処理します。 メニューがマウスによって開かれている場合でも、KeyTip はメニューを閉じるようになっています。|
|提案される解決策|N/A|
|スコープ|エッジ|
|Version|4.7.2|
|型|ランタイム|
