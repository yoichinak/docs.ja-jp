---
title: '方法: Windows サービスをインストールおよびアンインストールする'
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 4f6e25467e713263ab5cdecc08078153098fdede
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690679"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>方法: Windows サービスをインストールおよびアンインストールする

.NET Framework を使用して Windows サービスを開発している場合は、[*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) コマンド ライン ユーティリティを使用してサービス アプリをすばやくインストールできます。 ユーザーがインストールおよびアンインストールできる Windows サービスをリリースする開発者は、InstallShield を使用する必要があります。 詳細については、「[インストーラー パッケージを作成する (Windows デスクトップ)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client)」を参照してください。

> [!WARNING]
> サービスをコンピューターからアンインストールする場合は、この記事の手順には従わないでください。 代わりに、サービスをインストールしたプログラムまたはソフトウェア パッケージを確認し、[設定] で **[アプリ]** を選択してそのプログラムをアンインストールします。 多くのサービスが Windows の不可欠な構成要素であることに注意してください。それらを削除すると、システムが不安定になることがあります。

この記事の手順を使用するには、まず、Windows サービスにサービス インストーラーを追加する必要があります。 詳細については、「[チュートリアル:Windows サービス アプリケーションを作成する](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)」を参照してください。

Windows サービス プロジェクトを、F5 キーを押して Visual Studio 開発環境から直接実行することはできません。 プロジェクトを実行するには、プロジェクトにサービスを事前にインストールする必要があります。

> [!TIP]
> **サーバー エクスプローラー**を使用して、サービスがインストールまたはアンインストールされているかどうかを確認できます。 詳細については、[Visual Studio でのサーバー エクスプローラーの使用方法](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio)に関するページを参照してください。

### <a name="install-your-service-manually"></a>サービスを手動でインストールする

1. **[スタート]** メニューから **[Visual Studio \<*バージョン*>]** ディレクトリを選択し、 **[開発者コマンド プロンプト for VS \<*バージョン*>]** を選択します。

     Visual Studio 用開発者コマンド プロンプトが表示されます。

2. プロジェクトのコンパイル済み実行可能ファイルが格納されているディレクトリに移動します。

3. プロジェクトの実行可能ファイルをパラメーターとして指定し、コマンド プロンプトから *InstallUtil.exe* を実行します。

    ```console
    installutil <yourproject>.exe
    ```

     Visual Studio 用開発者コマンド プロンプトを使用している場合、*InstallUtil.exe* はシステム パス上にあるはずです。 ない場合は、パスに追加するか、完全修飾パスを使用して起動します。 .NET framework でこのツールがインストールされている *%windir%\microsoft.net\framework[64]\\< framework_version\>* します。

     次に例を示します。
     - 32 ビット バージョンの .NET Framework 4 または 4.5 以降では、Windows のインストール ディレクトリが *C:\Windows* の場合、既定のパスは *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe* です。
     - 64 ビット バージョンの .NET Framework 4 または 4.5 以降では、既定のパスは *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe* です。

### <a name="uninstall-your-service-manually"></a>サービスを手動でアンインストールする

1. **[スタート]** メニューから **[Visual Studio \<*バージョン*>]** ディレクトリを選択し、 **[開発者コマンド プロンプト for VS \<*バージョン*>]** を選択します。

     Visual Studio 用開発者コマンド プロンプトが表示されます。

2. プロジェクトの出力先ファイルをパラメーターとして指定し、コマンド プロンプトから *InstallUtil.exe* を実行します。

    ```console
    installutil /u <yourproject>.exe
    ```

3. 実行可能ファイルを削除した後も、レジストリ内にサービスが存在したままになることがあります。 このような場合は、コマンド [sc delete](/windows-server/administration/windows-commands/sc-delete) を使って、レジストリからサービスのエントリを削除します。

## <a name="see-also"></a>関連項目

- [Windows サービス アプリケーションの概要](../windows-services/introduction-to-windows-service-applications.md)
- [方法: Windows サービスを作成する](../windows-services/how-to-create-windows-services.md)
- [方法: サービス アプリケーションにインストーラーを追加する](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (インストーラー ツール)](../tools/installutil-exe-installer-tool.md)
