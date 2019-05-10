---
title: MDAInfo 構造体
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: faa6af54714f7f0b7ac91c7836673c163195d5f6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656458"
---
# <a name="mdainfo-structure"></a>MDAInfo 構造体
詳細について説明します、 `Event_MDAFired` 、マネージ デバッグ アシスタント (MDA) の作成をトリガーするイベントです。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`lpMDACaption`|現在の MDA のタイトル。 タイトルが発生したエラーの種類について説明します、`Event_MDAFired`イベント。|  
|`lpMDAMessage`|現在の MDA によって提供される出力メッセージです。|  
  
## <a name="remarks"></a>Remarks  
 マネージ デバッグ アシスタント (Mda) がランタイム実行エンジンでデバッグ共通言語ランタイム (CLR) で無効な条件を識別するなどのタスクを実行すると連携して動作する支援ツールまたはの状態に関する追加情報をダンプしますエンジン。 Mda は、トラップが困難な場合はイベントに関する XML メッセージを生成します。 マネージ コードとアンマネージ コード間の遷移をデバッグするために特に便利です。  
  
 MDA の作成をトリガーするイベントが発生したときに、ランタイムは、次の手順を受け取ります。  
  
- ホストが登録されていない場合、 [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)呼び出すことによってインスタンス[iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)の通知を受け取る、`Event_MDAFired`ランタイムを実行イベント、その既定では、ホストなしの動作。  
  
- ホストには、このイベントのハンドラーが登録されている場合、ランタイムは、デバッガーがプロセスにアタッチされているかどうかを確認します。 場合は、ランタイムはデバッガーを中断します。 デバッガーが引き続き発生する場合は、ホストを呼び出します。 デバッガーがアタッチされていない場合、ランタイムが呼び出す`IActionOnCLREvent::OnEvent`へのポインターを渡すと、`MDAInfo`インスタンスとして、`data`パラメーター。  
  
 Mda をアクティブ化して、MDA がアクティブ化されたときに通知するホストを選択できます。 これにより、ホストは、既定の動作をオーバーライドして、プロセスの状態の破損を防ぐために、イベントを発生させたマネージ スレッドを中止できます。 詳細については、Mda を使用して、次を参照してください。[マネージ デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.idl  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [マネージド デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
