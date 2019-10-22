---
title: Windows 互換機能パックを使用してコードを .NET Core に移植する
description: Windows 互換機能パックとそれを使用して既存の .NET Framework コードを .NET Core に移植する方法について紹介します。
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: adf2aaab27b5a8afcc89fceac67184d3b1974037
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521280"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Windows 互換機能パックを使用してコードを .NET Core に移植する

既存のコードを .NET Core に移植する際に発生する最も一般的な問題の一部として、.NET Framework のみに存在する API およびテクノロジへの依存があります。 *Windows 互換機能パック*には、このようなテクノロジの多くが用意されているので、.NET Core アプリケーションと .NET Standard ライブラリをはるかに簡単に構築できます。

このパッケージは論理 [.NET Standard 2.0 の拡張](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support)であり、API セットを大幅に増やします。ほとんど変更なしで既存コードがコンパイルされます。 ただし、.NET Standard の約束 ("これはあらゆる .NET 実装の API を集めたものである") を守る目的で、レジストリ、Windows Management Instrumentation (WMI)、リフレクション出力 API など、すべてのプラットフォームで動作しないテクノロジは含まれていません。

*Windows 互換機能パック*は .NET Standard を基盤とし、Windows 専用のテクノロジを利用できます。 .NET Core に移行したいが、最初の手順が Windows に留まることである顧客にとって特に便利です。 そのようなシナリオでは、Windows 専用テクノロジを利用できないことが移行における唯一のハードルとなります。アーキテクチャ上の利点がありません。

## <a name="package-contents"></a>パッケージの内容

*Windows 互換機能パック*は NuGet パッケージ [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) 経由で提供され、.NET Core または .NET Standard を対象とするプロジェクトから参照できます。

Windows 専用 API やプラットフォーム非依存 API など、約 20,000 の API を提供します。テクノロジ領域には次のものがあります。

- コード ページ
- CodeDom
- 構成
- ディレクトリ サービス
- 描画
- ODBC
- アクセス許可
- ポート
- Windows アクセス制御リスト (ACL)
- Windows Communication Foundation (WCF)
- Windows 暗号化
- Windows EventLog
- WMI (Windows Management Instrumentation)
- Windows パフォーマンス カウンター
- Windows レジストリ
- Windows ランタイム キャッシュ
- Windows サービス

詳細については、[互換機能パックの仕様](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)に関するページを参照してください。

## <a name="get-started"></a>作業開始

1. 移植の前に、[移植プロセス](index.md)を確認してください。

2. .NET Core または .NET Standard に既存のポートを移植するとき、NuGet パッケージ [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) をインストールします。

3. Windows に留まる場合、すでに用意はできています。

4. .NET Core アプリケーションまたは .NET Standard ライブラリを Linux または macOS で実行する場合、[API Analyzer](../../standard/analyzers/api-analyzer.md) を使用し、プラットフォーム非依存で機能しない API の使用を見つけます。

5. そのような API の使用を取り除くか、プラットフォーム非依存の代替で置換するか、プラットフォーム チェックで保護します (以下参照)。

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

デモについては、[Windows 互換機能パックの Channel 9 動画](https://channel9.msdn.com/Events/Connect/2017/T123)をご覧ください。
