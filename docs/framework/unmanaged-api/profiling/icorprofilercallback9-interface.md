---
title: ICorProfilerCallback9 インターフェイス
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1711def5e2aa41fd63912361ef8250ad160fb88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227757"
---
# <a name="icorprofilercallback9-interface"></a>ICorProfilerCallback9 インターフェイス
[.NET Framework 4.7.2 以降のバージョンでサポートされます]  

 サブクラス[ICorProfilerCallback8](icorprofilercallback8-interface.md)に動的メソッドがガベージ コレクションされ、その後にアンロードされたことをプロファイラーに通知する、共通言語ランタイムによって使用されるコールバック メソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DynamicMethodUnloaded メソッド](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|動的メソッドがガベージ コレクションされ、その後にアンロードされたことをプロファイラーに通知します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerCallback8 インターフェイス](icorprofilercallback9-interface.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationStarted メソッド](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationFinished メソッド](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
