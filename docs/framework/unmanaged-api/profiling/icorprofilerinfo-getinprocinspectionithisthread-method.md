---
title: ICorProfilerInfo::GetInprocInspectionIThisThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24b7af4b44d51da06e9d65104f1b469ef1d83b8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992070"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>ICorProfilerInfo::GetInprocInspectionIThisThread メソッド
ICorDebugThread インターフェイスのクエリを実行できるオブジェクトを取得します。 このメソッドは、.NET Framework version 2.0 で廃止されています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppicd`  
 [out](/cpp/atl/iunknown)オブジェクトのクエリを実行できる、`ICorDebugThread`インターフェイス。  
  
## <a name="remarks"></a>Remarks  
 サービスのデバッグ共通言語ランタイム (CLR) では、.NET Framework version 1.0 での限られたインプロセス デバッグがサポートされています。 インプロセス デバッグするには、デバッグ API の検査の部分を使用するプロファイラーを有効になっています。 お客様からのフィードバックの結果としてインプロセス デバッグがバージョン 2.0、.NET Framework から削除され、プロファイル API に合わせてさらには、機能のセットに置き換えられます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
