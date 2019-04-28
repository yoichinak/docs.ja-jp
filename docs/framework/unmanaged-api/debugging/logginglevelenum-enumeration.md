---
title: LoggingLevelEnum 列挙型
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe8e1355382273a681e927897f4a8ff5814b8de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765428"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum 列挙型
マネージド スレッドがイベントを記録する際にイベント ログに書き込まれる説明メッセージの重大度レベルを示します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`LTraceLevel0`|メッセージは、トレース レベル 0 です。|  
|`LTraceLevel1`|メッセージは、トレース レベル 1 です。|  
|`LTraceLevel2`|メッセージは、トレース レベル 2 です。|  
|`LTraceLevel3`|メッセージは、トレース レベル 3 です。|  
|`LTraceLevel4`|メッセージは、トレース レベル 4 です。|  
|`LStatusLevel0`|メッセージは、状態レベル 0 です。|  
|`LStatusLevel1`|メッセージは、レベル 1 の状態です。|  
|`LStatusLevel2`|メッセージは、状態のレベル 2 です。|  
|`LStatusLevel3`|メッセージは、状態レベル 3 です。|  
|`LStatusLevel4`|メッセージは、状態のレベル 4 です。|  
|`LWarningLevel`|メッセージは、警告レベルです。|  
|`LErrorLevel`|メッセージは、エラー レベルです。|  
|`LPanicLevel`|メッセージは、重大レベルです。|  
  
## <a name="remarks"></a>Remarks  
 共通言語ランタイム (CLR) の呼び出し、 [icordebugmanagedcallback::logmessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)マネージ スレッドがイベントを記録するデバッガーに通知するメソッド。 CLR の値を渡す、`LoggingLevelEnum`マネージ スレッドは、イベント ログに書き込まれたメッセージの重大度レベルを示す列挙体。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.EventLog>
- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
