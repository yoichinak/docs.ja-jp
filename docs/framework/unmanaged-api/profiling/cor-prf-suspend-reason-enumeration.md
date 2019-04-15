---
title: COR_PRF_SUSPEND_REASON 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21533b5173bcd91d0c944fbde4eafc9817de8315
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220059"
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON 列挙型
ランタイムが中断された理由を示します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|不明な理由により、ランタイムは中断されます。|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|ガベージ コレクションの要求にサービス ランタイムは中断されます。<br /><br /> ガベージ コレクションに関連するコールバックの間に発生、 [icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)と[icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)コールバック。|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|ランタイムは、中断できるように、`AppDomain`シャット ダウンすることができます。<br /><br /> どのスレッドは、ランタイムが決定されます、ランタイムが中断されている間、`AppDomain`はシャット ダウンして復帰するときに中止するように設定されています。 あるない`AppDomain`-この中断の間の特定のコールバック。|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|コード ピッチが実行できるように、ランタイムは中断されます。<br /><br /> コード ピッチが場合にのみ、ジャストイン タイム (JIT) コンパイラ active コード ピッチが有効になっているが発生します。 ピッチングのコールバックの間で発生するコード、`ICorProfilerCallback::RuntimeSuspendFinished`と`ICorProfilerCallback::RuntimeResumeStarted`コールバック。 **注:** この値は 2.0 では使用されないように、CLR JIT は、.NET Framework version 2.0 で関数をピッチいないします。|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|ランタイムが中断されるため、シャット ダウンできます。 操作を完了するすべてのスレッドが中断する必要があります。|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|ランタイムは、インプロセス デバッグの中断します。|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|ランタイムは、ガベージ コレクションの準備を中断します。|  
|`COR_PRF_SUSPEND_FOR_REJIT`|ランタイムの JIT 再コンパイルは中断されます。|  
  
## <a name="remarks"></a>Remarks  
 アンマネージ コードに含まれるすべてのランタイム スレッドは、この時点で、中断されます、ランタイムが再開されるまで、実行時の再入力するまで実行を続行が許可されます。 これは、ランタイムに入る新しいスレッドにも適用されます。 ランタイム内のすべてのスレッドは可能なコード内にある場合はすぐに中断または、割り込み可能なコードに到達したときに中断します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
