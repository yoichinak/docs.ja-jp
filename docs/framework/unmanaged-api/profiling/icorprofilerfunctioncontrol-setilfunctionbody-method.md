---
title: ICorProfilerFunctionControl::SetILFunctionBody メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d831dd7a63c06327bb0f373b3be254401c6e2ee9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780353"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a>ICorProfilerFunctionControl::SetILFunctionBody メソッド
メソッドの中間共通言語 (CIL) 本体を置換します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cbNewILMethodHeader`  
 [入力] ヘッダー、および本体の後に続く構造を含む、新しい CIL の合計サイズ。  
  
 `pbNewILMethodHeader`  
 [入力] 新しい CIL ヘッダーへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT を返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|置換が成功しました。|  
  
## <a name="remarks"></a>Remarks  
 異なり、 [icorprofilerinfo::setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)メソッド、`SetILFunctionBody`メソッドは、新しい CIL の本体に必要なメモリを管理します。 つまり、割り当てを使用して、プロファイラーが提供する CIL 本体がないこと、 [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)インターフェイスまたは特定の範囲内で割り当てられます。 この本体は、どのヒープにも割り当てることができます。 プロファイラーは、後、CIL 本体で使用されるメモリを解放できます`SetILFunctionBody`を返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerFunctionControl インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
