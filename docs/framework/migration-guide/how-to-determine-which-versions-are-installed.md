---
title: '方法: インストールされている .NET Framework バージョンを確認する'
ms.date: 02/20/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584175"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>方法: インストールされている .NET Framework バージョンを確認する

ユーザーはコンピューターに複数のバージョンの .NET Framework をインストールして実行できます。 アプリを開発または配置する場合、どのバージョンの .NET Framework がユーザーのコンピューターにインストールされているかを確認しなければならない場合があります。 .NET Framework は、個別にバージョン管理される 2 つの主要コンポーネントで構成されています。  
  
- アプリに機能を提供する型やリソースのコレクションである一連のアセンブリ。 .NET Framework とアセンブリは同じバージョン番号を共有します。  
  
- アプリのコードを管理および実行する共通言語ランタイム (CLR)。 CLR は独自のバージョン番号で識別されます (「[バージョンおよび依存関係](~/docs/framework/migration-guide/versions-and-dependencies.md)」を参照してください)。  
  
コンピューターにインストールされている .NET Framework バージョンの正確な一覧を取得するには、レジストリを表示するか、コードでレジストリを照会することができます。  
  
 [レジストリで .NET Framework バージョン 1 ～ 4 を探す](#net_a)  
 [レジストリで .NET Framework バージョン 4.5 以降を探す](#net_b)  
 [コードによるレジストリの照会 (バージョン 1 ～ 4)](#net_c)  
 [コードによるレジストリの照会 (バージョン 4.5 以降)](#net_d)  
 [PowerShell を使用したレジストリの照会 (バージョン 4.5 以降)](#ps_a)  

 CLR のバージョンを検索するには、ツールまたはコードを使用できます。  
  
 [Clrver ツールの使用](#clr_a)  
 [コードによる System.Environment クラスの照会](#clr_b)  

> [!NOTE]
> .NET Framework のバージョンと共通言語ランタイム (CLR) のバージョンの間には違いがあります。 .NET Framework は、.NET Framework のクラス ライブラリを構成するアセンブリのセットに基づいてバージョン管理されています。 たとえば、.NET Framework のバージョンには、4.5、4.6.1、および 4.7.2 が含まれます。 CLR は .NET Framework アプリケーションが実行されるランタイムに基づいてバージョン管理されており、通常、CLR の 1 つのバージョンでは .NET Framework の複数のバージョンがサポートされています。 CLR バージョン 4.30319.*xxxxx* では .NET Framework バージョン 4 ～ 4.5.2 がサポートされており、CLR バージョン 4.30319.42000 では .NET Framework 4.6 以降がサポートされています。 詳細については、<xref:System.Environment.Version?displayProperty=nameWithType> プロパティを参照してください。

 .NET Framework の各バージョン用にインストールされている更新プログラムの検出については、「[方法:インストールされている .NET Framework の更新プログラムを確認する](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)」を参照してください。 .NET Framework のインストールの詳細については、「[開発者向けの .NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md)」を参照してください。  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a>レジストリで .NET Framework バージョン 1 ～ 4 を探す 
  
1.  **[スタート]** ボタンをクリックし、**[ファイル名を指定して実行]** をクリックします。  
  
2.  **[開く]** ボックスに「**regedit.exe**」と入力します。  
  
     regedit.exe を実行するには、管理特権が必要です。  
  
3.  レジストリ エディターで、次のサブキーを開きます。  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     .NET Framework バージョン 1.1 ～ 3.5 の場合、インストールされているバージョンは、`NDP` サブキーの下のサブキーとして列挙されます。 バージョン番号は、バージョン サブキーの **Version** エントリに格納されています。 
     
     .NET Framework 4 の場合は、**Version** エントリは `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` サブキーと `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` サブキーのどちらか一方または両方の下にあります。

    > [!NOTE]
    > レジストリの ".NET Framework セットアップ" フォルダーの先頭はピリオドではありません。

    次の図では、.NET Framework 3.5 のサブキーと共にその **Version** エントリが示されています。

     ![.NET Framework 3.5 のレジストリ エントリ。](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET Framework 4 以前のバージョン")

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>レジストリで .NET Framework バージョン 4.5 以降を探す

1. **[スタート]** ボタンをクリックし、**[ファイル名を指定して実行]** をクリックします。

2. **[開く]** ボックスに「**regedit.exe**」と入力します。

     regedit.exe を実行するには、管理特権が必要です。

3. レジストリ エディターで、次のサブキーを開きます。

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     `Full` サブキーへのパスに `.NET Framework` ではなく `Net Framework` サブキーが含まれていることに注意してください。

    > [!NOTE]
    > `Full` サブキーが存在しない場合は、.NET Framework 4.5 以降がインストールされていません。

     `Release` という名前の DWORD 値を確認します。 `Release` DWORD がある場合は、.NET Framework 4.5 以降がそのコンピューターにインストールされています。 その値は、.NET Framework の特定のバージョンに対応するリリース キーです。 たとえば、次の図では、`Release` DWORD の値は 378389 で、これは .NET Framework 4.5 のリリース キーです。 

     ![.NET Framework 4.5 のレジストリ エントリ。](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

次の表では、.NET Framework の各バージョンに対する `Release` DWORD の最小値の一覧を示します。 これらの値は次のように使用できます。

- .NET Framework の最小バージョンが存在するかどうかを確認するには、レジストリの `Release` DWORD 値が表で示されている値と "*等しいかそれより大きい*" かどうかを調べます。 たとえば、アプリケーションで .NET Framework 4.7 以降が必要な場合は、最小のリリース キー値 460798 について調べます。

- 複数のバージョンについて調べるには、.NET Framework の最新のバージョンから始めて、以前のバージョンに順番に遡りながら調べます。

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|.NET Framework のバージョン|Release DWORD の値|
|--------------------------------|-------------|
|.NET Framework 4.5|378389|
|.NET Framework 4.5.1|378675|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.6|393295|
|.NET Framework 4.6.1|394254|
|.NET Framework 4.6.2|394802|
|.NET Framework 4.7|460798|
|.NET Framework 4.7.1|461308|
|.NET Framework 4.7.2|461808|

Windows オペレーティング システムの特定のバージョンに対する .NET Framework のリリース キーの完全な表については、「[.NET Framework のリリース キーと Windows オペレーティング システムのバージョン](release-keys-and-os-versions.md)」をご覧ください。

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a>コードで .NET Framework バージョン 1 ～ 4 を探す

- Windows レジストリ内の `HKEY_LOCAL_MACHINE` ブランチの下にある `Software\Microsoft\NET Framework Setup\NDP\` サブキーにアクセスするには、<xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> クラスを使用します。

     このクエリの例を次のコードに示します。

    > [!NOTE]
    > このコードでは、.NET Framework 4.5 以降を検出する方法は示されていません。 前のセクションで説明したように、これらのバージョンを検出するには、`Release` DWORD を確認してください。 .NET Framework 4.5 以降のバージョンを検出するコードについては、この記事の次のセクションを参照してください。

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a>コードで .NET Framework バージョン 4.5 以降を探す

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` キーに `Release` DWORD がある場合は、.NET Framework 4.5 以降がコンピューターにインストールされていることを示します。 キーワードの値はインストールされているバージョンを示します。 このキーワードを調べるには、<xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> および <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> メソッドを使用して、Windows レジストリのサブキーにアクセスします。

2. `Release` キーワードの値を確認して、インストールされているバージョンを決定します。 上位互換性を確認するには、「[レジストリで .NET Framework バージョン 4.5 以降を探す](#net_b)」セクションの表で示されている値と等しいかそれより大きい値を調べます。

レジストリの `Release` 値を確認して .NET Framework 4.5 以降のバージョンがインストールされているかどうかを判断する例を次に示します。

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

この例では、バージョンのチェックで推奨されている方法に従います。

- `Release` エントリの値が既知のリリース キー値*以上*かどうかをチェックします。

- 最新バージョンから最も古いバージョンの順にチェックします。

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>PowerShell を使用して最低限必要な .NET Framework のバージョン (4.5 以降) を確認する

次の例では、`Release` キーワードの値を確認して、.NET Framework 4.6.2 以降がインストールされているかどうかを判断します (インストールされている場合は `True` が返され、それ以外の場合は `False` が返されます)。

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a>Clrver.exe を使用して現在の CLR のバージョンを調べる

CLR バージョン ツール (Clrver.exe) を使用して、コンピューターにインストールされている共通言語ランタイムのバージョンを確認します。

Visual Studio 用開発者コマンド プロンプトで「`clrver`」と入力します。 次のような出力が表示されます。

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

このツールの使用については、「[Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md)」を参照してください。

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a>Environment クラスを使用して現在の CLR のバージョンを調べる

<xref:System.Environment.Version?displayProperty=nameWithType> プロパティの値を取得して <xref:System.Version> オブジェクトを取得し、現在コードを実行しているランタイムのバージョンを識別できます。 このプロパティでは、現在コードを実行しているランタイムのバージョンを表す単一の値が返されますが、アセンブリのバージョンやコンピューターにインストールされている可能性があるランタイムの他のバージョンは返されません。メジャー リリースの識別子 (バージョン 4.0 の "4" など) を取得するには <xref:System.Version.Major%2A?displayProperty=nameWithType> プロパティを、マイナー リリースの識別子 (バージョン 4.0 の "0" など) を取得するには <xref:System.Version.Minor%2A?displayProperty=nameWithType> プロパティを、バージョン文字列全体 (次のコードに示すような "4.0.30319.18010" など) を取得するには <xref:System.Version.ToString%2A?displayProperty=nameWithType> メソッドを使用できます。 

.NET Framework バージョン 4、4.5、4.5.1、および 4.5.2 の場合は、<xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティから返される <xref:System.Version> オブジェクトの文字列表現が `4.0.30319.xxxxx` という形式になっています。 .NET Framework 4.6 以降の場合は、`4.0.30319.42000` という形式です。

> [!IMPORTANT]
> .NET Framework 4.5 以降の場合、ランタイムのバージョンの検出に <xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティを使用することは推奨されません。 代わりに、この記事で前述した「[コードでレジストリを照会して .NET Framework のバージョンを検索するには (.NET Framework 4.5 以降)](#net_d)」に従って、レジストリを紹介することをお勧めします。

次の例では、<xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティを使用してランタイム バージョンの情報を取得しています。

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>関連項目

- [方法: インストールされている .NET Framework の更新プログラムを確認する](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [開発者向けの .NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md)
- [バージョンおよび依存関係](~/docs/framework/migration-guide/versions-and-dependencies.md)
