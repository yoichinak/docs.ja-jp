---
title: ServiceModel 登録ツール (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051789"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>ServiceModel 登録ツール (ServiceModelReg.exe)
このコマンド ライン ツールは、単一コンピューター上で WCF および WF コンポーネントの登録を管理するための機能を提供します。 WCF および WF コンポーネントはインストール時に構成されるため、通常の状況ではこのツールを使用する必要はありません。 しかし、サービスのアクティブ化に関する問題が発生する場合は、このツールを使用してコンポーネントを登録できます。  
  
## <a name="syntax"></a>構文  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Remarks  
 ツールは次の場所にあります。  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
>  ServiceModel 登録ツールを実行するときに[!INCLUDE[wv](../../../includes/wv-md.md)]、 **Windows 機能**ダイアログことが反映されない、 **Windows Communication Foundation HTTP Activation** オプション**Microsoft .NET Framework 3.0**がオンにします。 **Windows 機能**ダイアログをクリックしてアクセスできる**開始**、順にクリックします**実行**」と入力し、 **OptionalFeatures**します。  
  
 次の表は、ServiceModelReg.exe で使用できるオプションを示します。  
  
|オプション|説明|  
|------------|-----------------|  
|`-ia`|WCF および WF のすべてのコンポーネントをインストールします。|  
|`-ua`|WCF および WF のすべてのコンポーネントをアンインストールします。|  
|`-r`|WCF および WF のすべてのコンポーネントを修復します。|  
|`-i`|-c で指定された WCF および WF のコンポーネントをインストールします。|  
|`-u`|-c で指定された WCF および WF のコンポーネントをアンインストールします。|  
|`-c`|コンポーネントをインストールまたはアンインストールします。<br /><br /> -httpnamespace – HTTP Namespace 予約<br />-tcpportsharing – TCP ポート共有サービス<br />-tcpactivation – TCP のアクティブ化サービス (.NET 4 クライアント プロファイルでサポートされていない)<br />(.NET 4 クライアント プロファイルでサポートされていない - namedpipeactivation-名前付きパイプのアクティブ化サービス<br />--MSMQ アクティブ化 msmqactivation (.NET 4 クライアント プロファイルでサポートされていません<br />-etw – ETW イベントの追跡マニフェスト (Windows Vista またはそれ以降)|  
|`-q`|Quiet モード (エラー ログのみ表示)|  
|`-v`|Verbose モード|  
|`-nologo`|著作権やバナー メッセージを表示しません。|  
|`-?`|ヘルプ テキストを表示します。|  
  
## <a name="fixing-the-fileloadexception-error"></a>FileLoadException エラーの修正  
 WCF の以前のバージョンをコンピューターにインストールした場合表示、`FileLoadFoundException`新規インストールを登録する ServiceModelReg ツールを実行するとエラーが発生します。 旧バージョンのインストールから手動でファイルを削除しても、machine.config 設定が元のままである限り、このエラーが発生する可能性があります。  
  
 エラー メッセージは、次のようになります。  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 System.ServiceModel Version 2.0.0.0 アセンブリが旧 CTP (Customer Technology Preview) リリースによってインストールされていたというエラー メッセージに注目する必要があります。 最新バージョンの System.ServiceModel アセンブリは、2.0.0.0 ではなく 3.0.0.0 です。 そのため、WCF の初期の CTP リリースがインストールされているが完全にアンインストールで、コンピューターの WCF の公式リリースをインストールする場合に、この問題が発生します。  
  
 ServiceModelReg.exe は、旧バージョンのエントリをクリーンアップすることも、新しいバージョンのエントリを登録することもできません。 唯一の回避策は、machine.config を手動で編集することです。このファイルは次の場所にあります。  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 64 ビット コンピューターで WCF を実行している場合も、この場所にある同じファイルを編集する必要があります。  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 このファイルを参照する XML ノードを見つけ"'system.servicemodel, Version 2.0.0.0 ="、および子ノードを削除します。 ファイルを保存し ServiceModelReg.exe を再実行すると、この問題は解決します。  
  
## <a name="examples"></a>使用例  
 次の例に、ServiceModelReg.exe ツールの最も一般的なオプションの使用方法を示します。  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
