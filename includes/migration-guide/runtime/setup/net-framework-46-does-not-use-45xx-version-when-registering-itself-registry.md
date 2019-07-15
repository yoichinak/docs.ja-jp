---
ms.openlocfilehash: 08c16f261338148619de2e484c73046b9d9a6bfe
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858435"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4.6 は、自分自身をレジストリに登録するときに 4.5.x.x バージョンを使用しない

|   |   |
|---|---|
|説明|予想されるように、.NET Framework 4.6 に対してレジストリ (<code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) に設定されるバージョン キーは、"4.5" ではなく "4.6" で始まります。 これらのレジストリ キーに依存してコンピューターにインストールされている .NET Framework のバージョンを特定するアプリは、4.6 が可能な新しいバージョンであり、前の 4.5.x リリースと互換性があることを認識するように、更新する必要があります。|
|提案される解決策|4\.5 のレジストリ キーを検索することによって .NET Framework 4.5 のインストールを調べるアプリを、4.6 も受け付けるように更新します。|
|スコープ|エッジ|
|Version|4.6|
|型|ランタイム|

