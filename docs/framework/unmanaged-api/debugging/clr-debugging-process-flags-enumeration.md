---
title: CLR_DEBUGGING_PROCESS_FLAGS 列挙体
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8321e5aeba435ca5f1398a9cb827a93ae821d686
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996360"
---
# <a name="clrdebuggingprocessflags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS 列挙体
使用される値を提供します、 [iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|このランタイムには、送信する非 catch アップ マネージ デバッガー イベントがあります。 キャッチアップおよび非 catch アップ イベントを区別する、「解説」を参照してください。|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|管理対象のイベントが保留中ですが、<xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>要求。|  
  
## <a name="remarks"></a>Remarks  
 キャッチアップ イベントには、プロセス、アプリケーション ドメイン、アセンブリ、モジュール、および現在の状態には、プロセスにアタッチした後、デバッガーになるスレッドの作成の通知が含まれます。 示されている非 catch-アップ イベント、`CLR_DEBUGGING_MANAGED_EVENT_PENDING`フラグを設定し、すべて他のデバッガー イベント、例外などを追加し、マネージ デバッグ アシスタント (MDA) 通知します。  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`フラグをランタイム終了例外とキャンセル可能なマネージ デバッガーをアタッチする要求を区別するために使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Metahost.idl、Metahost.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
