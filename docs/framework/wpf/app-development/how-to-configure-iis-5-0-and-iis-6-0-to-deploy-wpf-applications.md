---
title: '方法: WPF アプリケーションを配置するように IIS 5.0 および IIS 6.0 を構成する'
ms.date: 03/30/2017
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
ms.openlocfilehash: 6fa00c4ced8c05d056703560e5740689c6dcfe39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973669"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>方法: WPF アプリケーションを配置するように IIS 5.0 および IIS 6.0 を構成する

適切な [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] タイプを使用して構成されている限り、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションは、ほとんどの Web サーバーから配置することができます。 既定では、[!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] は、これらの [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプを使用して構成されますが、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] および [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] は違います。

このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを配置するように、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] および [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] を構成する方法について説明します。

> [!NOTE]
> チェックすることができます、 *UserAgent*システムがインストールされている .NET Framework を持つかどうかを確認するレジストリ内の文字列。 詳細と、スクリプトを検査する、 *UserAgent*システムに .NET Framework がインストールされているかどうかを特定するを参照してください文字列[を検出するかどうか、.NET Framework 3.0 がインストールされて](how-to-detect-whether-the-net-framework-3-0-is-installed.md)。

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>コンテンツの有効期限の設定を調整する

コンテンツの有効期限の設定を 1 分に調整する必要があります。 次の手順は、[!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] でこれを行う方法を説明します。

1. **[スタート]** メニューをクリックして、**[管理ツール]** をポイントして、**[インターネット インフォメーション サービス (IIS) マネージャー]** をクリックします。 コマンド ラインで「SystemRoot%\system32\inetsrv\iis.msc %」と入力して、このアプリケーションを起動することもできます。

2. **[Default Web Site]** ノードが見つかるまで、[!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] ツリーを展開します。

3. **[Default Web Site]** を右クリックし、コンテキスト メニューの **[プロパティ]** を選択します。

4. **[HTTP ヘッダー]** タブを選択し、[コンテンツの有効期限を有効にする をクリックします。

5. 1 分後に期限切れになるようにコンテンツを設定します。

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a>MIME タイプとファイル拡張子を登録する

クライアント システムのブラウザーで適切なハンドラーを読み込めるように、いくつかの [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプとファイル拡張子を登録する必要があります。 次のタイプを追加する必要があります。

|拡張子|[MIME の種類]|
|---------------|---------------|
|.manifest|application/manifest|
|.xaml|application/xaml+xml|
|.application|application/x-ms-application|
|.xbap|application/x-ms-xbap|
|.deploy|application/octet-stream|
|.xps|application/vnd.ms-xpsdocument|

> [!NOTE]
> クライアント システムに [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプとファイル拡張子を登録する必要はありません。 Microsoft .NET Framework をインストールするときに、自動的に登録します。

次の Microsoft Visual Basic Scripting Edition (VBScript) サンプルは、必要に応じて自動的に追加されます[!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)]型を[!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]します。 スクリプトを使用するには、サーバー上の .vbs ファイルにこのコードをコピーします。 その後、コマンド ラインからファイルを実行するか、[!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)] でファイルをダブルクリックして、スクリプトを実行します。

```vb
' This script adds the necessary Windows Presentation Foundation MIME types
' to an IIS Server.
' To use this script, just double-click or execute it from a command line.
' Running this script multiple times results in multiple entries in the IIS MimeMap.

Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec
Const ADS_PROPERTY_UPDATE = 2

' Set the MIME types to be added
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _
    "application/xaml+xml", ".application", "application/x-ms-application", _
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _
    ".xps", "application/vnd.ms-xpsdocument")

' Get the MimeMap object
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")

' Call AddMimeType for every pair of extension/MIME type
For counter = 0 to UBound(MimeTypesToAddArray) Step 2
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)
Next

' Create a Shell object
Set WshShell = CreateObject("WScript.Shell")

' Stop and Start the IIS Service
Set oExec = WshShell.Exec("net stop w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = WshShell.Exec("net start w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = Nothing

' Report status to user
WScript.Echo "Windows Presentation Foundation MIME types have been registered."

' AddMimeType Sub
Sub AddMimeType (Ext, MType)

    ' Get the mappings from the MimeMap property.
    MimeMapArray = MimeMapObj.GetEx("MimeMap")

    ' Add a new mapping.
    i = UBound(MimeMapArray) + 1
    ReDim Preserve MimeMapArray(i)
    Set MimeMapArray(i) = CreateObject("MimeMap")
    MimeMapArray(i).Extension = Ext
    MimeMapArray(i).MimeType = MType
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray
    MimeMapObj.SetInfo

End Sub
```

> [!NOTE]
> このスクリプトを複数回実行すると、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] メタベースに複数の [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] マップ エントリが作成されます。

このスクリプトを実行しても、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)] から追加の [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプを参照できない場合があります。 しかし、これらの [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプは、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] メタベースに追加されています。 次のスクリプトは、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] メタベース内のすべての [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプを表示します。

```vb
' This script lists the MIME types for an IIS Server.
' To use this script, just double-click or execute it from a command line
' by calling cscript.exe

dim mimeMapEntry, allMimeMaps

' Get the MimeMap object.
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")
allMimeMaps = mimeMapEntry.GetEx("MimeMap")

' Display the mappings in the table.
For Each mimeMap In allMimeMaps
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")
Next
```

スクリプトを `.vbs` ファイルとして保存し (たとえば、`DiscoverIISMimeTypes.vbs`)、次のコマンドを使用して、コマンド プロンプトから実行します。

```console
cscript DiscoverIISMimeTypes.vbs
```
