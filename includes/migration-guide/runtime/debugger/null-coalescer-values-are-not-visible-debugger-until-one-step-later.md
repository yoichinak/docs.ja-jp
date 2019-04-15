---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235414"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>デバッガーですぐに null コアレッサー値が表示されない

|   |   |
|---|---|
|説明|.NET Framework 4.5 のバグにより、64 ビット版の Framework で実行中に代入演算が実行された直後に、デバッガーで null 合体演算で設定された値が表示されません。|
|提案される解決策|デバッガーでの操作に時間がかかると、ローカル/フィールドの値が正しく更新されなくなります。 この問題は .NET Framework 4.6 で修正されました。このバージョンの .NET Framework にアップグレードすれば、問題は解決します。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
