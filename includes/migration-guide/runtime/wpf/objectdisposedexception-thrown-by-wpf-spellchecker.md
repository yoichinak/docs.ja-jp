---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234206"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException が WPF スペルチェックでスローされる

|   |   |
|---|---|
|説明|スペルチェックで <xref:System.ObjectDisposedException?displayProperty=name> がスローされ、WPF アプリケーションがシャットダウン時にクラッシュする場合があります。 これは .NET Framework 4.7 WPF で修正されます。例外は正しく処理されるため、アプリケーションが悪影響を受けることはなくなります。 ただし、デバッグ時に実行中のアプリケーションで初回例外が見られる場合があるので注意してください。|
|提案される解決策|.NET Framework 4.7 にアップグレードします|
|スコープ|エッジ|
|Version|4.6.1|
|型|ランタイム|
