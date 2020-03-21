---
title: FunctionIDMapper 関数
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175175"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper 関数
関数の指定された識別子が[、関数の FunctionEnter2](functionenter2-function.md) [、FunctionLeave2](functionleave2-function.md)、および[FunctionTailcall2](functiontailcall2-function.md)コールバックで使用される代替 ID に再マップされる可能性があることをプロファイラーに通知します。 また `FunctionIDMapper` により、プロファイラーはその関数のコールバックを受信するかどうかを示すことができます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>パラメーター

- `funcId`

  \[in] 再マップする関数識別子。

- `pbHookFunction`

  \[out] プロファイラーが 、 `true` 、および`FunctionEnter2``FunctionLeave2``FunctionTailcall2`コールバックを受け取る場合に設定する値へのポインター。それ以外の場合は、この`false`値を に設定します。

## <a name="return-value"></a>戻り値  
 プロファイラーは、実行エンジンが代替関数識別子として使用する値を返します。 `false` で `pbHookFunction` を返さない限り、戻り値を null にすることはできません。 それ以外の場合、null 戻り値は、プロセスを停止する可能性を含む、予測できない結果を生成します。  
  
## <a name="remarks"></a>解説  
 関数`FunctionIDMapper`はコールバックです。 プロファイラーは、関数 ID を、プロファイラーに役立つ他の識別子に再マップするために実装されます。 は`FunctionIDMapper`、任意の関数に使用される代替 ID を返します。 実行エンジンは、従来の関数 ID に加えて、この代替 ID を渡すことによってプロファイラーの要求を受け入れ、 `clientData` `FunctionEnter2`、`FunctionLeave2`および`FunctionTailcall2`フックのパラメーターのプロファイラーに戻して、フックが呼び出される関数を識別します。  
  
 関数の実装を指定するには、メソッドを使用します。 [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) `FunctionIDMapper` メソッドを呼び`ICorProfilerInfo::SetFunctionIDMapper`出すことができるのは 1 回だけであり[、ICorProfilerCallback::初期化](icorprofilercallback-initialize-method.md)コールバックで呼び出す方法をお勧めします。  
  
 既定では[、ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md)を使用してCOR_PRF_MONITOR_ENTERLEAVEフラグを設定し[、ICorProfilerInfo:::SetEnterLeaveFunctionHooks または ICorProfilerInfo2:::SetEnterLeaveFunctionHooks2](icorprofilerinfo-setenterleavefunctionhooks-method.md)を介してフックを設定するプロファイラー`FunctionEnter2`は`FunctionLeave2`、すべての`FunctionTailcall2`関数のコールバックを受け取る必要があると仮定されます。 [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) ただし、プロファイラーは`FunctionIDMapper`、 に設定`pbHookFunction`することで、特定の関数に対してこれらのコールバック`false`を受け取ることを選択的に回避するために実装できます。  
  
 プロファイラーは、プロファイルされたアプリケーションの複数のスレッドが同じメソッド/関数を同時に呼び出している場合に許容する必要があります。 このような場合、プロファイラーは`FunctionIDMapper`同じ`FunctionID`. プロファイラーは、同じ を使用して複数回呼び出された場合、このコールバックから同じ`FunctionID`値を返すようにしてください。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コルプロフ.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [SetFunctionIDMapper メソッド](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 関数](functionidmapper2-function.md)
- [FunctionEnter2 関数](functionenter2-function.md)
- [FunctionLeave2 関数](functionleave2-function.md)
- [FunctionTailcall2 関数](functiontailcall2-function.md)
- [グローバル静的関数のプロファイル](profiling-global-static-functions.md)
