---
title: ICorProfilerCallback::ObjectsAllocatedByClass メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f5d2c08abbcab6bc1a6d0569b8e70d7c919def
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195866"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass メソッド
最新のガベージ コレクションの後に作成された指定した各クラスのインスタンスの数をプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>パラメーター  
 `cClassCount`  
 [in]サイズ、`classIds`と`cObjects`配列。  
  
 `classIds`  
 [in]クラス Id、各 ID が 1 つまたは複数のインスタンスを持つクラスを指定の配列。  
  
 `cObjects`  
 [in]各整数が対応するクラスのインスタンスの数を指定します、整数の配列、`classIds`配列。  
  
## <a name="remarks"></a>Remarks  
 `classIds`と`cObjects`配列は並列配列です。 たとえば、`classIds[i]`と`cObjects[i]`同じクラスを参照します。 前のガベージ コレクションの後、クラスのインスタンスが作成されていない場合、クラスは省略されます。 `ObjectsAllocatedByClass`コールバックは、大きなオブジェクト ヒープに割り当てられたオブジェクトは報告されません。  
  
 によって、報告される`ObjectsAllocatedByClass`はのみ推定されます。 正確な数は、使用[icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)します。  
  
 `classIds`配列は 1 つまたは複数の null エントリを含めることができる場合、対応する`cObjects`配列がアンロードしている型。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
