---
title: ICorProfilerCallback::ManagedToUnmanagedTransition メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b00394d0b08e7e4a02b95437908dd65a51d0a042
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084610"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition メソッド
マネージ コードからアンマネージ コードへの移行が発生したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]呼び出される関数の ID。  
  
 `reason`  
 [in]値、 [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) 、マネージ コードからアンマネージ コードへの呼び出しによって、またはアンマネージによって呼び出されるマネージ関数の戻り値のために、移行が発生したかどうかを示す列挙体。  
  
## <a name="remarks"></a>Remarks  
 場合の値`reason`COR_PRF_TRANSITION_CALL、こと、アンマネージ関数は決してコンパイルされたジャスト イン タイム コンパイラを使用して ID は、関数は、します。 アンマネージ関数では、名前といくつかのメタデータなど、それに関連付けられている基本情報があります。 暗黙的なプラットフォームを使用して、アンマネージ関数が呼び出された場合は、呼び出し (PInvoke)、ランタイムは、呼び出しの変換先およびの値を判別できません`functionId`は null になります。 詳細については、暗黙の PInvoke は、次を参照してください。[を使用して C++ Interop (暗黙の PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [C++ での明示的な PInvoke (DllImport 属性) の使用方法](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
