---
ms.openlocfilehash: 39a329597ef28e002242103a247515d94761676a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234717"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>ResolveAssemblyReference タスクは、正しくないアーキテクチャとの依存関係に関する警告を表示するようになりました

|   |   |
|---|---|
|説明|タスクは警告 MSB3270 を生成します。これは参照または依存関係がアプリのアーキテクチャと一致しないことを示します。 たとえば、<code>AnyCPU</code> オプションでコンパイルされたアプリに x86 参照が含まれる場合に発生します。 このようなシナリオは、実行時にアプリでエラーが起こった場合に発生することがあります (この場合は、アプリが x64 プロセスとして配置されている場合)。|
|提案される解決策|影響には 2 つの領域があります。<ul><li>再コンパイルすると、アプリが MSBuild の以前のバージョンでコンパイルされたときには現れなかった警告が生成されます。 ただし、警告はランタイム エラーの可能性のある原因を特定するため、調査と対処が必要です。</li><li>警告がエラーとして扱われると、アプリはコンパイルされません。</li></ul>|
|スコープ|マイナー|
|Version|4.5.1|
|型|再ターゲット中|
