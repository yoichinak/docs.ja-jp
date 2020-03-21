---
title: ServiceModel 登録ツール (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183100"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>ServiceModel 登録ツール (ServiceModelReg.exe)
このコマンド ライン ツールは、単一コンピューター上で WCF および WF コンポーネントの登録を管理するための機能を提供します。 WCF および WF コンポーネントはインストール時に構成されるため、通常の状況ではこのツールを使用する必要はありません。 しかし、サービスのアクティブ化に関する問題が発生する場合は、このツールを使用してコンポーネントを登録できます。  
  
## <a name="syntax"></a>構文  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>解説  
 ツールは次の場所にあります。  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
> Windows Vista でサービス モデル登録ツールを実行すると **、Windows の機能**ダイアログ ボックスには **、Microsoft .NET Framework 3.0**の下の **[Windows 通信基盤] HTTP アクティブ化**オプションが有効になっていることが反映されない場合があります。 [スタート] ボタンをクリックし、[**ファイル****名を指定して実行**] をクリックし、「オプション機能」と入力すると **、[Windows の機能**] ダイアログ ボックスにアクセス**できます**。  
  
 次の表は、ServiceModelReg.exe で使用できるオプションを示します。  
  
|オプション|説明|  
|------------|-----------------|  
|`-ia`|WCF および WF のすべてのコンポーネントをインストールします。|  
|`-ua`|WCF および WF のすべてのコンポーネントをアンインストールします。|  
|`-r`|WCF および WF のすべてのコンポーネントを修復します。|  
|`-i`|-c で指定された WCF および WF のコンポーネントをインストールします。|  
|`-u`|-c で指定された WCF および WF のコンポーネントをアンインストールします。|  
|`-c`|コンポーネントをインストールまたはアンインストールします。<br /><br /> - http 名前空間 – HTTP 名前空間の予約<br />- tcpport 共有 – TCP ポート共有サービス<br />- tcp アクティベーション – TCP アクティベーション サービス (.NET 4 クライアント プロファイルではサポートされていません)<br />- 名前付きパイプのアクティブ化 – 名前付きパイプのアクティブ化サービス (.NET 4 クライアント プロファイルではサポートされていません)<br />- msmq アクティベーション – MSMQ ライセンス認証サービス (.NET 4 クライアント プロファイルではサポートされていません)<br />- etw – ETW イベント トレース マニフェスト (Windows Vista 以降)|  
|`-q`|Quiet モード (エラー ログのみ表示)|  
|`-v`|Verbose モード|  
|`-nologo`|著作権やバナー メッセージを表示しません。|  
|`-?`|ヘルプ テキストを表示します。|  
  
## <a name="fixing-the-fileloadexception-error"></a>FileLoadException エラーの修正  
 以前のバージョンの WCF をコンピューターにインストールした場合は、ServiceModelReg ツールを`FileLoadFoundException`実行して新しいインストールを登録するときにエラーが発生することがあります。 旧バージョンのインストールから手動でファイルを削除しても、machine.config 設定が元のままである限り、このエラーが発生する可能性があります。  
  
 エラー メッセージは、次のようになります。  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 System.ServiceModel Version 2.0.0.0 アセンブリが旧 CTP (Customer Technology Preview) リリースによってインストールされていたというエラー メッセージに注目する必要があります。 最新バージョンの System.ServiceModel アセンブリは、2.0.0.0 ではなく 3.0.0.0 です。 したがって、この問題は、WCF の初期の CTP リリースがインストールされているが、完全にアンインストールされていないコンピューターに、公式の WCF リリースをインストールする場合に発生します。  
  
 ServiceModelReg.exe は、旧バージョンのエントリをクリーンアップすることも、新しいバージョンのエントリを登録することもできません。 唯一の回避策は、machine.config を手動で編集することです。このファイルは、次の場所にあります。  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 64 ビット コンピューターで WCF を実行している場合は、この場所でも同じファイルを編集する必要があります。  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 "System.ServiceModel, バージョン = 2.0.0.0" を参照する XML ノードをこのファイル内で見つけ、それらと子ノードを削除します。 ファイルを保存し ServiceModelReg.exe を再実行すると、この問題は解決します。  
  
## <a name="examples"></a>例  
 次の例に、ServiceModelReg.exe ツールの最も一般的なオプションの使用方法を示します。  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
