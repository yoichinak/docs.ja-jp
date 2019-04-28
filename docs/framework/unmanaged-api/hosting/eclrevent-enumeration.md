---
title: EClrEvent 列挙型
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13d564be68d6b49a1616be97710312f33f828d48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628660"
---
# <a name="eclrevent-enumeration"></a>EClrEvent 列挙型
ホストがコールバックを登録できる共通言語ランタイム (CLR) のイベントについて説明します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`Event_ClrDisabled`|CLR の致命的なエラーを指定します。|  
|`Event_DomainUnload`|特定のアンロードを指定します。<xref:System.AppDomain>します。|  
|`Event_MDAFired`|マネージ デバッグ アシスタント (MDA) メッセージが生成されたことを指定します。|  
|`Event_StackOverflow`|スタックのオーバーフロー エラーが発生したことを指定します。|  
  
## <a name="remarks"></a>Remarks  
 ホストで説明されているイベントの種類のいずれかのコールバックを登録できる`EClrEvent`のメソッドを呼び出すことによって、 [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)インターフェイス。 ホストは、呼び出すことによってこのインターフェイスにポインターを取得、 [iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)メソッド。  
  
 `Event_CLRDisabled`と`Event_DomainUnload`2 回以上、アンロード、または CLR の無効化を通知する別のスレッドからイベントを発生させることができます。  
  
 `Event_MDAFired`イベント発生の作成、 [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) MDA メッセージの詳細を格納しているインスタンス。 Mda の詳細については、次を参照してください。[マネージ デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IActionOnCLREvent インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
