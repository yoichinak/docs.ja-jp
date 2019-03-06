---
title: ICorProfilerInfo::GetInprocInspectionInterface メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fbb4aa43757df86037d9c883e76ee38cef5eeb86
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494429"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a>ICorProfilerInfo::GetInprocInspectionInterface メソッド
"ICorDebugProcess"インターフェイスのクエリを実行できるオブジェクトを取得します。 このメソッドは、.NET Framework version 2.0 で廃止されています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppicd`  
 [out](/cpp/atl/iunknown)オブジェクトのクエリを実行できる、`ICorDebugProcess`インターフェイス。  
  
## <a name="remarks"></a>Remarks  
 デバッグ API 共通言語ランタイム (CLR) では、.NET Framework version 1.0 での限られたインプロセス デバッグがサポートされています。 インプロセス デバッグするには、デバッグ API の検査の部分を使用するプロファイラーを有効になっています。 お客様からのフィードバックの結果としてインプロセス デバッグがバージョン 2.0、.NET Framework から削除され、プロファイル API に合わせてさらには、機能のセットに置き換えられます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
