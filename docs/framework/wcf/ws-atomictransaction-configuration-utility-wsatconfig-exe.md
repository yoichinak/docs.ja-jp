---
title: WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 30e5a22e54bf977143b2ae94e678ad5106ec9ed6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191823"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)
WS-AtomicTransaction 構成ユーティリティは、基本的な WS-AtomicTransaction サポート設定を構成するために使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Remarks  
 このコマンド ライン ツールを使用して、基本的な WS-AtomicTransaction 設定をローカル マシンでのみ構成できます。 」の説明に従って、MMC スナップインで使用してくださいローカルとリモートの両方のマシンの設定を構成した場合[Ws-atomic トランザクションのサポートを構成する](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)します。  
  
 コマンド ライン ツールは、Windows SDK の次のインストール場所にあります。  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 [!INCLUDE[wxp](../../../includes/wxp-md.md)] または [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] を実行している場合は、更新プログラムをダウンロードしてから、WsatConfig.exe を実行する必要があります。 この更新プログラムの詳細については、次を参照してください。 [Commerce Server 2007 (KB912817) 用更新](https://go.microsoft.com/fwlink/?LinkId=95340)と[可用性の Windows XP COM + Hotfix Rollup Package 13](https://go.microsoft.com/fwlink/?LinkId=95341)します。  
  
 次の表は、WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe) で使用できるオプションを示します。  
  
> [!NOTE]
>  選択したポートに SSL 証明書を設定すると、そのポートに関連付けられたオリジナルの SSL 証明書が上書きされます。  
  
|オプション|説明|  
|-------------|-----------------|  
|-accounts:\<account,>|WS-AtomicTransaction に追加できるアカウントをコンマで区切って指定します。 これらのアカウントの有効性の確認は行われません。|  
|-accountsCerts:\<thumb>&#124;"Issuer\SubjectName",>|WS-AtomicTransaction に追加できる証明書をコンマで区切って指定します。 証明書は、サムプリントまたは Issuer\SubjectName ペアで示されます。 空の場合は、サブジェクト名に {EMPTY} を使用します。|  
|-endpointCert:<machine&#124;\<thumb>&#124;"Issuer\SubjectName">|コンピューターの証明書を使用するか、サムプリントまたは Issuer\SubjectName ペアで指定される別のローカル エンドポイントの証明書を使用します。 空の場合は、サブジェクト名に {EMPTY} を使用します。|  
|-maxTimeout:\<sec>|最大タイムアウトを秒単位で指定します。 有効な値は 0 ~ 3600 です。|  
|-network:\<enable&#124;disable>|WS-AtomicTransaction ネットワーク サポートを有効または無効にします。|  
|-port:\<portNum>|WS-AtomicTransaction の HTTPS ポートを設定します。<br /><br /> このツールを実行する前にファイアウォールが既に有効な場合、ポートは例外の一覧に自動的に登録されます。 このツールを実行する前にファイアウォールが無効な場合は、ファイアウォールに関する追加の構成はありません。<br /><br /> WS-AT の構成後にファイアウォールを有効にする場合は、このツールを再度実行し、このパラメーターを使用してポート番号を指定する必要があります。 WS-AT の構成後にファイアウォールを無効にする場合は、入力を追加しないで WS-AT の動作を続行します。|  
|タイムアウト:\<秒 >|既定のタイムアウトを秒単位で指定します。 有効な値は 1 ～ 3600 の範囲です。|  
|-traceActivity:\<enable&#124;disable>|アクティビティ イベントのトレースを有効または無効にします。|  
|-traceLevel:\<オフ&#124;エラー&#124;重要な&#124;警告&#124;情報&#124;詳細&#124;すべて >}|トレース レベルを指定します。|  
|-tracePII:\<enable&#124;disable>|個人を特定できる情報のトレースを有効または無効にします。|  
|-traceProp:\<enable&#124;disable>|伝達イベントのトレースを有効または無効にします。|  
|-restart|MSDTC を再起動して変更を直ちに反映します。 これが指定されていない場合、変更は、MSDTC が再起動されたときに有効になります。|  
|-show|現在の WS-AtomicTransaction プロトコル設定を表示します。|  
|-仮想サーバー:\<virtualServer >|DTC リソース クラスター名を指定します。|  
  
## <a name="see-also"></a>関連項目

- [WS-AtomicTransaction の使用](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)
- [WS-AtomicTransaction サポートの構成](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
