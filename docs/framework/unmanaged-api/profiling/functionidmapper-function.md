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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2de19252b5c978fef38124636e4098ae5ece1b0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097939"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper 関数
使用される代替 ID に、関数の指定した id 再割り当てされることをプロファイラーに通知、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)、および[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)その関数のコールバック。 `FunctionIDMapper` プロファイラーのコールバック関数を受信するかどうかを指定できます。  
  
## <a name="syntax"></a>構文  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `funcId`  
 [入力] 再割り当てされる関数識別子。  
  
 `pbHookFunction`  
 [out]プロファイラーに設定される値へのポインター`true`を受信する必要がある場合`FunctionEnter2`、 `FunctionLeave2`、および`FunctionTailcall2`コールバックです。 それ以外の場合、この値設定`false`します。  
  
## <a name="return-value"></a>戻り値  
 プロファイラーは、実行エンジンが代替関数識別子として使用する値を返します。 `false` で `pbHookFunction` を返さない限り、戻り値を null にすることはできません。 それ以外の場合、戻り値を null、プロセスの中止などの予期しない結果が生成されます。  
  
## <a name="remarks"></a>Remarks  
 `FunctionIDMapper`関数がコールバック。 プロファイラーの役に立つその他の何らかの識別子に関数の ID を再マップするために、プロファイラーによって実装されます。 `FunctionIDMapper`任意指定の関数に使用する代替 ID を返します。 実行エンジンでプロファイラーに戻るだけでなく、従来の関数の ID では、この代替 ID を渡すことによって、プロファイラーの要求からは優先、`clientData`のパラメーター、 `FunctionEnter2`、 `FunctionLeave2`、および`FunctionTailcall2`フックを識別するために対象のフック関数が呼び出される関数。  
  
 使用することができます、 [icorprofilerinfo::setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)メソッドの実装を指定する、`FunctionIDMapper`関数。 呼び出すことができます、`ICorProfilerInfo::SetFunctionIDMapper`とメソッドを 1 回のみで実行することをお勧めします、 [icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)コールバック。  
  
 既定では、ことが前提とプロファイラーをセットする COR_PRF_MONITOR_ENTERLEAVE フラグを使用して[icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)を使用してフックを設定して[icorprofilerinfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)または[icorprofilerinfo 2::setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)、受信する必要があります、 `FunctionEnter2`、 `FunctionLeave2`、および`FunctionTailcall2`の各関数にコールバックします。 ただし、プロファイラーが実装`FunctionIDMapper`選択的にこれらのコールバックを特定の受信を回避するために設定して関数`pbHookFunction`に`false`します。  
  
 プロファイラーは、プロファイリング対象のアプリケーションの複数のスレッドが、同じメソッド/関数を同時に呼び出す場合の必要があります。 このような場合は、プロファイラーが複数を受け取る可能性があります`FunctionIDMapper`のコールバックを同じ`FunctionID`します。 プロファイラーがあります同じを複数回呼び出された場合、このコールバックから同じ値が返されます特定`FunctionID`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [SetFunctionIDMapper メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 関数](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [FunctionEnter2 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
