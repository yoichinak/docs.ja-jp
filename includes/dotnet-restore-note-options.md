---
ms.openlocfilehash: 497ac09e5c9a10470d3ae1932d7e3dc114d121dd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632017"
---
> [!NOTE]
> .NET Core 2.0 以降、[`dotnet restore`](~/docs/core/tools/dotnet-restore.md) を実行する必要がなくなりました。`dotnet build` や `dotnet run` のような、復元を必要とするあらゆるコマンドによって暗黙的に実行されるためです。 [Azure DevOps Services の継続的インテグレーション ビルド](/azure/devops/build-release/apps/aspnet/build-aspnet-core)など、明示的な復元が合理的となる一部のシナリオや、復元の時刻を明示的に制御する必要があるビルド システムでは、引き続き有効なコマンドとなります。
>
> このコマンドには `dotnet restore` オプションを指定できますが、`--source` のように長い形式で指定する必要があります。 `-s` のような短い形式のオプションはサポートされていません。
