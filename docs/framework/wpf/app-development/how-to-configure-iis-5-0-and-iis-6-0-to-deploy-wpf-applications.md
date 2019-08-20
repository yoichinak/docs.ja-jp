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
ms.openlocfilehash: 3a9bf79a9d505fef53b62cb589920adcf95ae92a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611507"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>方法: WPF アプリケーションを配置するように IIS 5.0 および IIS 6.0 を構成する

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションは、適切な Multipurpose Internet Mail Extensions (MIME) の種類で構成されていれば、ほとんどの Web サーバーから展開できます。 既定では、Microsoft インターネットインフォメーションサービス (IIS) 7.0 はこれらの MIME の種類で構成されていますが、Microsoft インターネットインフォメーションサービス (IIS) 5.0 および Microsoft インターネットインフォメーションサービス (IIS) 6.0 は構成されていません。

このトピックでは、microsoft インターネットインフォメーションサービス (iis) 5.0 と microsoft インターネットインフォメーションサービス (iis) 6.0 を構成し[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]てアプリケーションを展開する方法について説明します。

> [!NOTE]
> レジストリの*UserAgent*文字列を確認して、システムに .NET Framework がインストールされているかどうかを確認できます。 *UserAgent*文字列を調べて .NET Framework がシステムにインストールされているかどうかを確認するスクリプトについては、「 [.NET Framework 3.0 がインストールされているかどうかを検出](how-to-detect-whether-the-net-framework-3-0-is-installed.md)する」を参照してください。

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>コンテンツの有効期限の設定を調整する

コンテンツの有効期限の設定を 1 分に調整する必要があります。 次の手順では、IIS でこれを行う方法について説明します。

1. **[スタート]** メニューをクリックして、 **[管理ツール]** をポイントして、 **[インターネット インフォメーション サービス (IIS) マネージャー]** をクリックします。 コマンド ラインで「SystemRoot%\system32\inetsrv\iis.msc %」と入力して、このアプリケーションを起動することもできます。

2. **[既定の Web サイト]** ノードが表示されるまで、IIS ツリーを展開します。

3. **[Default Web Site]** を右クリックし、コンテキスト メニューの **[プロパティ]** を選択します。

4. **HTTP ヘッダー** タブを選択し、コンテンツの有効期限を有効にする をクリックします。

5. 1 分後に期限切れになるようにコンテンツを設定します。

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a>MIME タイプとファイル拡張子を登録する

クライアントのシステムのブラウザーが適切なハンドラーを読み込めるように、いくつかの MIME の種類とファイル拡張子を登録する必要があります。 次のタイプを追加する必要があります。

|拡張子|[MIME の種類]|
|---------------|---------------|
|.manifest|application/manifest|
|.xaml|application/xaml+xml|
|.application|application/x-ms-application|
|.xbap|application/x-ms-xbap|
|.deploy|application/octet-stream|
|.xps|application/vnd.ms-xpsdocument|

> [!NOTE]
> クライアントシステムに MIME の種類またはファイル拡張子を登録する必要はありません。 これらは Microsoft .NET Framework のインストール時に自動的に登録されます。

次の Microsoft Visual Basic Scripting Edition (VBScript) のサンプルでは、必要な MIME の種類が IIS に自動的に追加されます。 スクリプトを使用するには、サーバー上の .vbs ファイルにこのコードをコピーします。 その後、コマンド ラインからファイルを実行するか、[!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)] でファイルをダブルクリックして、スクリプトを実行します。

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
> このスクリプトを複数回実行すると、Microsoft インターネットインフォメーションサービス (IIS) 5.0 または Microsoft インターネットインフォメーションサービス (IIS) 6.0 メタベースに複数の MIME マップエントリが作成されます。

このスクリプトを実行すると、Microsoft インターネットインフォメーションサービス (IIS) 5.0 または Microsoft インターネットインフォメーションサービス (IIS) 6.0 Microsoft 管理コンソール (MMC) で追加された MIME の種類が表示されない場合があります。 ただし、これらの MIME の種類は、Microsoft インターネットインフォメーションサービス (IIS) 5.0 または Microsoft インターネットインフォメーションサービス (IIS) 6.0 メタベースに追加されています。 次のスクリプトでは、Microsoft インターネットインフォメーションサービス (IIS) 5.0 または Microsoft インターネットインフォメーションサービス (IIS) 6.0 メタベースのすべての MIME の種類が表示されます。

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
