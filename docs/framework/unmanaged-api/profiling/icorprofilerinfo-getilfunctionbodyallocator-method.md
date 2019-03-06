---
title: ICorProfilerInfo::GetILFunctionBodyAllocator メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 432ebff36f3b4ee0362e01fc5ecd1bfdb35bc493
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493012"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator メソッド
Microsoft intermediate language (MSIL) コード内のメソッドの本文をスワップするために使用されるメモリを割り当てるメソッドを提供するインターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleId`  
 [in]メソッドが存在するモジュールの ID。  
  
 `ppMalloc`  
 [out]ポインター、 [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)メモリを割り当てるメソッドを提供するインターフェイスです。  
  
## <a name="remarks"></a>Remarks  
 メソッドの本体の MSIL コードでは、4 GB 内のモジュールに従っていることを意味、読み込まれたモジュールの基準とした相対仮想アドレス (RVA) として配置である必要があります。 メソッドの本体のスワップ アウトするためのツールを容易にできるように、`GetILFunctionBodyAllocator`メソッドにより、メモリがその範囲内で割り当てられます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
