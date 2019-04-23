---
title: CorDebugUserState 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54b2af6e7a200db89bfd7335868a629d7a886fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141311"
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState 列挙型
スレッドのユーザーの状態を示します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>メンバー  
  
|[値]|説明|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|スレッドの終了が要求されています。|  
|`USER_SUSPEND_REQUESTED`|スレッドの中断が要求されています。|  
|`USER_BACKGROUND`|スレッドのバック グラウンドで実行します。|  
|`USER_UNSTARTED`|スレッドが実行を開始していません。|  
|`USER_STOPPED`|スレッドが終了しました。|  
|`USER_WAIT_SLEEP_JOIN`|スレッドがタスクを完了する別のスレッドを待機しています。|  
|`USER_SUSPENDED`|スレッドが中断されました。|  
|`USER_UNSAFE_POINT`|スレッドは、安全でない点になります。 これは、スレッドがある実行の時点でガベージ コレクションを妨げること可能性があります。<br /><br /> デバッグ、安全でないポイントからイベントをディスパッチすることがありますが、安全でない時点でスレッドを中断する、多くの場合、デッドロックが発生、スレッドが再開されるまでです。 安全性と安全でないポイントは、- イン タイム (JIT) およびガベージ コレクションの実装によって決まります。|  
|`USER_THREADPOOL`|スレッドはスレッド プールです。|  
  
## <a name="remarks"></a>Remarks  
 スレッドのユーザー状態とは、状態、スレッドがデバッガーを調べることでです。 スレッドは、ユーザー状態の組み合わせがあります。  
  
 使用して、 [icordebugthread::getuserstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)スレッドのユーザーの状態を取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
