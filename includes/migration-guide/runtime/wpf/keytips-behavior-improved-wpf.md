---
ms.openlocfilehash: d7cf32eb369e2607ee540d7188cc680b9506c261
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856926"
---
### <a name="keytips-behavior-improved-in-wpf"></a>WPF での KeyTip の動作が改良された

|   |   |
|---|---|
|説明|KeyTip の動作が、Microsoft Word やエクスプローラーでの動作と同等に変更されています。 <xref:System.Windows.Input.KeyEventArgs.SystemKey> (具体的には <xref:System.Windows.Input.Key> または <xref:System.Windows.Input.Key.F11>) が押された場合に KeyTip の状態が有効かどうかを調べることによって、WPF は KeyTip キーを適切に処理します。 メニューがマウスによって開かれている場合でも、KeyTip はメニューを閉じるようになっています。|
|提案される解決策|N/A|
|スコープ|エッジ|
|Version|4.7.2|
|型|ランタイム|

