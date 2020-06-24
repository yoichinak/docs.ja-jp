---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602718"
---

[dotnet-install スクリプト](../../tools/dotnet-install-script.md)は、**SDK** のインストールの自動化および管理者以外によるインストールに使用されます。 このスクリプトは <https://dot.net/v1/dotnet-install.sh> からダウンロードできます。

スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。 (LTS) バージョンではない場合がある現在のリリースをインストールするには、`-c Current` パラメーターを使用します。

```bash
./dotnet-install.sh -c Current
```

SDK の代わりに .NET Core ランタイムをインストールするには、`--runtime` パラメーターを使用します。

```bash
./dotnet-install.sh -c Current --runtime
```

特定のバージョンをインストールするには、`-c` パラメーターを変更して特定のバージョンを指定します。 次のコマンドでは、.NET Core SDK 3.1 がインストールされます。

```bash
./dotnet-install.sh -c 3.1
```

詳細については、「[dotnet-install スクリプト リファレンス](../../tools/dotnet-install-script.md)」をご覧ください。
