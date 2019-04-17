---
ms.openlocfilehash: 1805c26f1eff46719f30de8a14ca6d35f01948a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234759"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>foreach 反復子変数は、イテレーション内をスコープとするようになったため、クロージャ キャプチャのセマンティクスが (C#5 では) 異なります。

|   |   |
|---|---|
|説明|C#5 (Visual Studio 2012) 以降では、<code>foreach</code> 反復子変数は、イテレーション内をスコープとします。 このため、変数が <code>foreach</code> のクロージャに含まれないことに依存していたコードは機能しなくなります。 この変更による症状は、デリゲートに渡された反復子変数が、デリゲートが呼び出された時点での値ではなく、デリゲートの作成時点での値として扱われることです。|
|提案される解決策|理想的には、新しいコンパイラの動作を予期するように、コードを更新する必要があります。 古いセマンティクスが必要な場合は、反復子変数を、ループのスコープ外に明示的に配置される別の変数に置き換えることができます。|
|スコープ|Major|
|バージョン|4.5|
|型|再ターゲット中|
