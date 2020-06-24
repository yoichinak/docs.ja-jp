---
title: .NET Core と Linux ディストリビューションをインストールする
description: Linux への .NET Core のインストールをサポートしている Linux ディストリビューションについて説明します。
author: thraka
ms.author: adegeo
ms.date: 06/01/2020
ms.openlocfilehash: fec3cf9e99c2db5d7312280f676bc2a3344f1ae1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602670"
---
# <a name="install-net-core-on-linux"></a>Linux に .NET Core をインストールする

.NET Core は、さまざまな Linux ディストリビューションで使用できます。 ほとんどの Linux プラットフォームおよびディストリビューションには毎年メジャー リリースがあり、そのほとんどでは .NET Core のインストールに使用されるパッケージ マネージャーが提供されます。 この記事では、現在何がサポートされているかと、どのパッケージ マネージャーが使用されるかについて説明します。

この記事の残りの部分では、.NET Core でサポートされている主要な各 Linux ディストリビューションの詳細について説明します。 すべての .NET Core リリースは、[.NET Core のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、Linux ディストリビューションのバージョンがサポート終了になるまでサポートされます。

互換性を最大限に高めるために、長期的なリリース (LTS) のバージョンを選択してください。

## <a name="unsupported-releases"></a>サポートされていないリリース

次のバージョンの .NET Core は ❌ サポート対象外となりました。 これらのダウンロードは、まだ公開されています。

- 3.0
- 2.2
- 2.0

これらのサポートされていないバージョンについては、以下のセクションでは詳しく説明しません。これらをインストールしようとする場合、実現できることが変動する可能性があります。

## <a name="centos"></a>CentOS

CentOS 7 ではパッケージ マネージャーとして Yum が使用され、CentOS 8 では DNF が使用されます。

次の表は、CentOS 7 と CentOS 8 の両方で現在サポートされている .NET Core リリースの一覧です。 これらのバージョンは、[.NET Core のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、CentOS のバージョンがサポート終了になるまでサポートされます。

| CentOS                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (手動インストールのみ) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

詳細については、[CentOS での .NET Core のインストール](linux-centos.md)に関する記事をご覧ください。

## <a name="debian"></a>Debian

Debian では、パッケージ マネージャーとして APT (Advanced Package Tool) が使用されます。

次の表は、現在サポートされている .NET Core リリースと、それらがサポートされている Debian のバージョンの一覧です。 これらのバージョンは、[.NET Core のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Debian のバージョンがサポート終了になる](https://wiki.debian.org/DebianReleases)までサポートされます。

- ✔️ は、Debian または .NET Core のバージョンがまだサポートされていることを示します。
- ❌ は、Debian または .NET Core のバージョンがその Debian のリリースではサポートされていないことを示しています。
- Debian のバージョンと .NET Core のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| Debian                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (手動インストールのみ) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ❌ [8](linux-debian.md#debian-8-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |

## <a name="fedora"></a>Fedora

Fedora では、パッケージ マネージャーとして DNF が使用されます。

次の表は、現在サポートされている .NET Core リリースと、それらがサポートされている Fedora のバージョンの一覧です。 これらのバージョンは、[.NET Core のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Fedora のバージョンがサポート終了になる](https://fedoraproject.org/wiki/End_of_life)までサポートされます。

- ✔️ は、Fedora または .NET Core のバージョンがまだサポートされていることを示します。
- ❌ は、Fedora または .NET Core のバージョンがその Fedora のリリースではサポートされていないことを示しています。
- Fedora のバージョンと .NET Core のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| Fedora                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (手動インストールのみ) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [31](linux-fedora.md#fedora-31-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ❌ [30](linux-fedora.md#fedora-30-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 Preview |
| ❌ [29](linux-fedora.md#fedora-29-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 Preview |
| ❌ [28](linux-fedora.md#fedora-28-) | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |
| ❌ [27](linux-fedora.md#fedora-27-) | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |

詳細については、[Fedora での .NET Core のインストール](linux-fedora.md)に関する記事をご覧ください。

## <a name="opensuse"></a>openSUSE

openSUSE では、パッケージ マネージャーとして zypper が使用されます。

次の表は、openSUSE 15 で現在サポートされている .NET Core リリースの一覧です。 これらのバージョンは、[.NET Core のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、openSUSE のバージョンがサポート終了になるまでサポートされます。

- ✔️ は、openSUSE または .NET Core のバージョンがまだサポートされていることを示します。
- ❌ は、openSUSE または .NET Core のバージョンがその openSUSE のリリースではサポートされていないことを示しています。
- openSUSE のバージョンと .NET Core のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (手動インストールのみ) |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux (RHEL) では、パッケージ マネージャーとして yum (RHEL 7) と DNF (RHEL 8) が使用されます。

次の表は、RHEL 7 と RHEL 8 の両方で現在サポートされている .NET Core リリースの一覧です。 これらのバージョンは、[.NET Core のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、RHEL のバージョンがサポート終了になるまでサポートされます。

- ✔️ は、RHEL または .NET Core のバージョンがまだサポートされていることを示します。
- ❌ は、RHEL または .NET Core のバージョンがその RHEL のリリースではサポートされていないことを示しています。
- RHEL のバージョンと .NET Core のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| RHEL                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (手動インストールのみ) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [7](linux-rhel.md#rhel-7-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

## <a name="sles"></a>SLES

SLES では、パッケージ マネージャーとして zypper が使用されます。

次の表は、SLES 12 SP2 と SLES 15 の両方で現在サポートされている .NET Core リリースの一覧です。 これらのバージョンは、[.NET Core のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、SLES のバージョンがサポート終了になるまでサポートされます。

- ✔️ は、SLES または .NET Core のバージョンがまだサポートされていることを示します。
- ❌ は、SLES または .NET Core のバージョンがその SLES のリリースではサポートされていないことを示しています。
- SLES のバージョンと .NET Core のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (手動インストールのみ) |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [12 SP2](linux-sles.md#sles-12-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

## <a name="ubuntu"></a>Ubuntu

Ubuntu では、パッケージ マネージャーとして APT (Advanced Package Tool) が使用されます。

次の表は、Ubuntu と .NET Core のサポート状態を示しています。

- ✔️ は、Ubuntu または .NET Core のバージョンがまだサポートされていることを示します。
- ❌ は、Ubuntu または .NET Core のバージョンがその Ubuntu のリリースではサポートされていないことを示しています。
- Ubuntu のバージョンと .NET Core のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (手動インストールのみ) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20.04 (LTS)](linux-ubuntu.md#2004-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ✔️ [19.10](linux-ubuntu.md#1910-)       | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ❌ [19.04](linux-ubuntu.md#1904-)       | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 Preview |
| ❌ [18.10](linux-ubuntu.md#1810-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |
| ✔️ [18.04 (LTS)](linux-ubuntu.md#1804-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |
| ❌ [17.10](linux-ubuntu.md#1710-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |
| ❌ [17.04](linux-ubuntu.md#1704-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |
| ❌ [16.10](linux-ubuntu.md#1610-)       | ❌ 2.1        | ❌ 3.1        | ❌ 5.0 Preview |
| ✔️ [16.04 (LTS)](linux-ubuntu.md#1604-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 Preview |

詳細については、[Ubuntu での .NET Core のインストール](linux-ubuntu.md)に関する記事をご覧ください。
