---
title: .NET Framework 1.1 からの移行
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 441a65f9a72dd0fcffb062710df74bb529767cef
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816063"
---
# <a name="migrating-from-the-net-framework-11"></a>.NET Framework 1.1 からの移行

[!INCLUDE[win7](../../../includes/win7-md.md)] 以降のバージョンの Windows オペレーティング システムは、.NET Framework 1.1 をサポートしていません。 その結果、.NET Framework 1.1 を対象とするアプリケーションは実行されません変更せず[!INCLUDE[win7](../../../includes/win7-md.md)]以降のオペレーティング システムのバージョン。 このトピックでは、.NET Framework 1.1 を対象とするアプリケーションを実行するために必要な手順を説明します[!INCLUDE[win7](../../../includes/win7-md.md)]と以降のバージョンの Windows オペレーティング システム。 .NET Framework 1.1 の詳細については、[!INCLUDE[win8](../../../includes/win8-md.md)]を参照してください[Windows 8 およびそれ以降のバージョンの .NET Framework 1.1 アプリを実行している](../../../docs/framework/install/run-net-framework-1-1-apps.md)します。

## <a name="retargeting-or-recompiling"></a>再ターゲットまたは再コンパイル

2 つの方法で実行する .NET Framework 1.1 を使用してコンパイルされたアプリケーションを取得する[!INCLUDE[win7](../../../includes/win7-md.md)]以降の Windows オペレーティング システム。

- .NET Framework 4 以降のバージョンで動作するようにアプリケーションのターゲットを変更することができます。 再ターゲットするには、[\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 要素をアプリケーションの構成ファイルに追加して .NET Framework 4 以降のバージョンで動作できるようにする必要があります。 そのための構成ファイルの形式は次のとおりです。

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- .NET Framework 4 以降のバージョンをターゲットとするコンパイラでアプリケーションを再コンパイルできます。 最初に Visual Studio 2003 を使用してソリューションを開発およびコンパイルした場合は、ソリューションを Visual Studio 2010 で (そしておそらく以降のバージョンでも) で開くことができます。また、 **[Project Compatibility]\(プロジェクト互換性\)** ダイアログ ボックスを使用して、ソリューションおよびプロジェクト ファイルを Visual Studio 2003 で使用される形式から Microsoft Build Engine (MSBuild) 形式に変換することができます。

再コンパイルまたは再ターゲットのいずれを選択するかに関係なく、アプリケーションが .NET Framework の新しいバージョンで導入された変更の影響を受けるかどうかを確認する必要があります。 変更には次の 2 種類があります。

- .NET Framework 1.1 と .NET Framework の以降のバージョン間で発生した重大な変更。

- 型と非推奨としてマークされている、または .NET Framework 1.1 と .NET Framework の以降のバージョン間で廃止された型のメンバー。

アプリケーションを再ターゲットまたは再コンパイルするかどうか、重大な変更と旧式の型および .NET Framework 1.1 にリリースされた .NET Framework のバージョンごとにメンバーを確認してください。

## <a name="breaking-changes"></a>互換性に影響する変更点

互換性に影響する変更が行われた場合は、変更内容に応じて、アプリケーションの再ターゲットおよび再コンパイル時の回避策が提示される場合があります。 場合によっては、アプリケーションの構成ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 要素に子要素を追加することで、以前の動作を復元できます。 たとえば、次の構成ファイルは、文字列の並べ替えを復元し、比較の動作は、.NET Framework 1.1 で使用され、再ターゲットまたは再コンパイルされたアプリケーションで使用することができます。

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

ただし、ソース コードの変更とアプリケーションの再コンパイルが必要になる場合があります。

互換性に影響する可能性がある変更点がアプリケーションに与える影響を評価するには、次の変更一覧を確認する必要があります。

- [.NET Framework 2.0 における重大な変更](https://go.microsoft.com/fwlink/?LinkId=125263)を .NET Framework 1.1 を対象とするアプリケーションに影響を与える、.NET Framework 2.0 SP1 での変更について説明します。

- [.NET Framework 3.5 SP1 で変更](https://go.microsoft.com/fwlink/?LinkID=186989)、.NET Framework 3.5 の間の変更について説明し、[!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)]します。

- 「[.NET Framework 4 への移行に関する問題](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)」に記載されている、[!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] から .NET Framework 4 の変更点。

## <a name="obsolete-types-and-members"></a>旧式の型およびメンバー

非推奨の型およびメンバーの影響は、アプリケーションを再ターゲットする場合と再コンパイルする場合とでは若干異なります。 旧式の型およびメンバーを使用しても、その型およびメンバーをアセンブリから物理的に削除しない限り、再ターゲットしたアプリケーションには影響しません。 旧式の型およびメンバーを使用してアプリケーションを再コンパイルすると、通常はコンパイラ エラーではなく、コンパイラの警告が発生します。 ただし、場合によってはコンパイラ エラーが発生し、旧式の型またはメンバーを使用したコードをコンパイルできないことがあります。 その場合は、旧式の型またはメンバーを呼び出すソース コードを変更してからアプリケーションを再コンパイルする必要があります。 旧式の型およびメンバーの詳細については、「[.NET Framework クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)」を参照してください。

型と .NET Framework 2.0 SP1 のリリース以降非推奨になったメンバーの影響を評価するには、次を参照してください。[クラス ライブラリで廃止は](../../../docs/framework/whats-new/whats-obsolete.md)します。 .NET Framework 2.0 SP1、.NET Framework 3.5 および .NET Framework 4 の旧式の型およびメンバーの一覧を確認します。
