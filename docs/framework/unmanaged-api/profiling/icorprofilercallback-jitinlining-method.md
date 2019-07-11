---
title: ICorProfilerCallback::JITInlining メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82af06837ead9a00923c23d4ce145015308fbbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782801"
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining メソッド
別の関数に合わせて関数を挿入しようとしています-イン タイム (JIT) コンパイラがプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>パラメーター  
 `callerId`  
 [in]先の関数の ID、`calleeId`関数が挿入されます。  
  
 `calleeId`  
 [in]挿入する関数の ID。  
  
 `pfShouldInline`  
 [out]`true`発生挿入を許可する場合は、`false`します。  
  
## <a name="remarks"></a>Remarks  
 プロファイラーを設定できます`pfShouldInline`に`false`を防ぐために、`calleeId`関数に挿入されてから、`callerId`関数。 また、プロファイラー グローバルに無効にできますインライン挿入の COR_PRF_DISABLE_INLINING 値を使用して、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙体。  
  
 挿入関数をインラインでは、出入りに関するイベントは発生しません。 そのため、プロファイラーを設定する必要があります`pfShouldInline`に`false`正確なコールグラフを生成するためにします。 設定`pfShouldInline`に`false`インライン挿入は通常速度が向上し、挿入されたメソッドの別の JIT コンパイル イベントの数が減るため、パフォーマンスに影響します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
