---
title: .NET フレームワークと .NET コアの違い
description: Windows プレゼンテーション ファンデーション (WPF) と .NET コア WPF の .NET フレームワーク実装の違いについて説明します。 アプリを移行する際には、これらの非互換性を考慮する必要があります。
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 4386654aad205e3c9f2cbd986d7b812e261e737f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "81433134"
---
# <a name="differences-in-wpf"></a>WPF の違い

この資料では、.NET コアと .NET Framework の Windows プレゼンテーション ファンデーション (WPF) の違いについて説明します。 .NET Core の WPF は、元の WPF から .NET Framework ソース コードをフォークされた[オープン ソース フレームワーク](https://github.com/dotnet/wpf)です。

.NET Framework には、.NET Core でサポートされていない機能がいくつかあります。 サポートされていないテクノロジの詳細については、「 [.NET Framework テクノロジは .NET Core では使用できません](../../core/porting/net-framework-tech-unavailable.md)」を参照してください。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>SDK スタイルのプロジェクト

.NET Core では、SDK スタイルのプロジェクト ファイルを使用します。 これらのプロジェクト ファイルは、Visual Studio によって管理される従来の .NET Framework プロジェクト ファイルとは異なります。 .NET Framework WPF アプリを .NET Core に移行するには、プロジェクトを変換する必要があります。 詳細については、「 [.NET Core 3.0 への WPF アプリの移行](convert-project-from-net-framework.md)」を参照してください。

## <a name="nuget-package-references"></a>NuGet パッケージのリファレンス

.NET Framework アプリが、その NuGet 依存関係を*packages.config*ファイルに[`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files)一覧表示する場合は、次の形式に移行します。

1. Visual Studio で、[**ソリューション エクスプローラー** ] ウィンドウを開きます。
1. WPF プロジェクトで、[**パッケージ.config パッケージ.config** > **をパッケージ参照に移行**する] を右クリックします。

![パッケージリファレンスへのアップグレード](media/differences-from-net-framework/package-reference-migration.png)

計算された最上位レベルの NuGet 依存関係を示すダイアログが表示され、他のどの NuGet パッケージを最上位レベルに昇格するかを確認します。 **[OK] を**選択すると *、packages.config*ファイルがプロジェクト`<PackageReference>`から削除され、要素がプロジェクト ファイルに追加されます。

プロジェクトで を`<PackageReference>`使用する場合、パッケージは*Packages*フォルダーにローカルに保存されません。 プロジェクト ファイルを開き`<Analyzer>`*、Packages*フォルダーを参照している要素を削除します。 これらのアナライザーは、NuGet パッケージ参照に自動的に含まれます。

## <a name="code-access-security"></a>コード アクセス セキュリティ

コード アクセス セキュリティ (CAS) は、.NET コアまたは .NET コアの WPF ではサポートされていません。 CAS 関連のすべての機能は、完全信頼の前提で処理されます。 .NET コアの WPF は、CAS 関連のコードを削除します。 これらの型への呼び出しが成功するために、これらの型のパブリック API サーフェスは依然として存在します。

パブリックに定義された CAS 関連の型は、WPF アセンブリから CoreFX アセンブリに移動されました。 WPF アセンブリは、移動された型の新しい場所に設定された型転送を持っています。

| ソース アセンブリ | ターゲット アセンブリ | Type                |
| --------------- | --------------- | ------------------- |
| *WindowsBase.dll* | *アクセス許可.dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *System.Xaml.dll* | *アクセス許可.dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *System.Xaml.dll* | *システム.Windows.エクステンション.dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> 移植摩擦を最小限に抑えるために、以下のプロパティに関連する情報を保存および取得する機能は`XamlAccessLevel`、このタイプに保持されていました。
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>次のステップ

- [.NET Framework WPF アプリを .NET Core に移植する方法について説明します。](convert-project-from-net-framework.md)
