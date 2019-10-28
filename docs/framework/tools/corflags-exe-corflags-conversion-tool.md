---
title: CorFlags.exe (CorFlags 変換ツール)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63e70ae8cd110786ad7d2069088dbfdfde736a28
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846744"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags 変換ツール)
CorFlags 変換ツールを使用して、ポータブル実行可能 (PE) ファイル イメージのヘッダー内の CorFlags セクションを設定できます。  
  
 このツールは、Visual Studio と共に自動的にインストールされます。 このツールを実行するには、Visual Studio 用開発者コマンド プロンプト (または Windows 7 の Visual Studio コマンド プロンプト) を使用します。 詳細については、「[Visual Studio 用開発者コマンド プロンプト](developer-command-prompt-for-vs.md)」を参照してください。  
  
 コマンド プロンプトに次のように入力します。  
  
## <a name="syntax"></a>構文  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a>パラメーター  
  
|必須パラメーター|説明|  
|------------------------|-----------------|  
|`assembly`|CorFlags を設定するアセンブリの名前。|  
  
|オプション|説明|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|32BITREQUIRED フラグを設定します。|  
|`-32BIT[REQ]-`|32BITREQUIRED フラグをクリアします。|  
|`-32BITPREF+`|32BITPREFERRED フラグを設定します。 アプリは、64 ビット プラットフォーム上でも 32 ビット プロセスとして実行します。 このフラグは、EXE ファイルでのみ設定します。 このフラグを DLL で設定した場合、64 ビット プロセスで DLL を読み込むことができず、<xref:System.BadImageFormatException> 例外がスローされます。 このフラグを設定した EXE ファイルは、64 ビット プロセスで読み込むことができます。<br /><br /> .NET Framework 4.5 で新たに追加されました。|  
|`-32BITPREF-`|32BITPREFERRED フラグをクリアします。<br /><br /> .NET Framework 4.5 で新たに追加されました。|  
|`-?`|このツールのコマンド構文とオプションを表示します。|  
|`-Force`|厳密な名前が付けられているアセンブリであっても、強制的に更新します。 **重要:** 厳密な名前が付けられているアセンブリを更新する場合は、そのコードを実行する前に再署名する必要があります。|  
|`-help`|このツールのコマンド構文とオプションを表示します。|  
|`-ILONLY+`|ILONLY フラグを設定します。|  
|`-ILONLY-`|ILONLY フラグをクリアします。|  
|`-nologo`|Microsoft 著作権情報を表示しません。|  
|`-RevertCLRHeader`|CLR ヘッダー バージョンを 2.0 に戻します。|  
|`-UpgradeCLRHeader`|CLR ヘッダー バージョンを 2.5 にアップグレードします。 **注:** アセンブリをネイティブに実行するには、CLR ヘッダー バージョン 2.5 以降が必要です。|  
  
## <a name="remarks"></a>解説  
 オプションが何も指定されていない場合、CorFlags 変換ツールは指定されているアセンブリのフラグを表示します。  
  
## <a name="see-also"></a>関連項目

- [ツール](index.md)
- [64 ビット アプリケーション](../64-bit-apps.md)
- [Visual Studio 用開発者コマンド プロンプト](developer-command-prompt-for-vs.md)
