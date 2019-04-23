---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774230"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException が WPF スペルチェックでスローされる

|   |   |
|---|---|
|説明|スペルチェックで <xref:System.ObjectDisposedException?displayProperty=name> がスローされ、WPF アプリケーションがシャットダウン時にクラッシュする場合があります。 これは .NET Framework 4.7 WPF で修正されます。例外は正しく処理されるため、アプリケーションが悪影響を受けることはなくなります。 ただし、デバッグ時に実行中のアプリケーションで初回例外が見られる場合があるので注意してください。|
|提案される解決策|.NET Framework 4.7 にアップグレードします|
|スコープ|エッジ|
|Version|4.6.1|
|型|ランタイム|
