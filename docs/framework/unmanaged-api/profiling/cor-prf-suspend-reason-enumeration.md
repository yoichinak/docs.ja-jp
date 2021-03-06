---
title: "COR_PRF_SUSPEND_REASON 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SUSPEND_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SUSPEND_REASON
helpviewer_keywords: COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713360b3cdc30ce7bca3e0df115016d66e59b0df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
|`COR_PRF_FIELD_SUSPEND_OTHER`|ランタイムは、不明な理由の中断されています。|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|ランタイムは、ガベージ コレクションの要求の処理を中断します。<br /><br /> ガベージ コレクションに関連するコールバックの間で発生する、 [icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)と[icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)コールバック。|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|ランタイムが中断されているように、`AppDomain`シャット ダウンできます。<br /><br /> ランタイムが中断されている間、ランタイムはスレッドを判別に、`AppDomain`はシャット ダウンされ、中断するときに設定しています。 ない`AppDomain`-この保留中の特定のコールバック。|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|コード ピッチを実行できるように、ランタイムが中断されます。<br /><br /> コード ピッチ ・ イン タイム (JIT) コンパイラがのときだけアクティブなコード ピッチが有効になっているが発生します。 ピッチング コールバックの間で発生するコード、`ICorProfilerCallback::RuntimeSuspendFinished`と`ICorProfilerCallback::RuntimeResumeStarted`コールバック。 **注:** 2.0 でこの値は使用されませんので、CLR JIT が .NET framework version 2.0 では、関数をピッチされません。|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|ランタイムは中断、終了できるようにします。 操作を完了するすべてのスレッドを中断にする必要があります。|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|ランタイムは、プロセスのデバッグの中断されています。|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|ランタイムがガベージ コレクションの準備に中断されます。|  
|`COR_PRF_SUSPEND_FOR_REJIT`|ランタイムは、JIT 再コンパイルの中断されています。|  
  
## <a name="remarks"></a>コメント  
 アンマネージ コード内にあるすべてのランタイムのスレッドは、この時点で、中断されます、ランタイムが再開されるまで、ランタイムを再入力するまで実行を続行が許可されます。 これは、新しいスレッドがランタイムに入ることにも適用されます。 ランタイム内のすべてのスレッドが可能なコード内にある場合、すぐに中断されているか、中断可能なコードに到達したときに中断します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
