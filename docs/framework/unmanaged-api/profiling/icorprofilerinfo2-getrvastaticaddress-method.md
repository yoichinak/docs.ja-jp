---
title: ICorProfilerInfo2::GetRVAStaticAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3749c600d54671071efbec8322e050cde446c27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791626"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a>ICorProfilerInfo2::GetRVAStaticAddress メソッド
指定された相対仮想アドレス (RVA) の静的フィールドのアドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>パラメーター  
 `classId`  
 [in]要求の RVA 静的フィールドを含むクラスの ID。  
  
 `fieldToken`  
 [in]要求された静的 RVA フィールドのメタデータ トークン。  
  
 `ppAddress`  
 [out]RVA 静的フィールドのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `GetRVAStaticAddress`メソッドは、次のいずれかを返す可能性があります。  
  
- 指定された静的フィールドに指定したコンテキスト内のアドレスが割り当てられていない場合の CORPROF_E_DATAINCOMPLETE HRESULT。  
  
- ガベージ コレクション ヒープで可能性のあるオブジェクトのアドレス。 これらのアドレスは、ガベージ コレクション後にプロファイラーを想定しないでくださいが有効であるために、ガベージ コレクションの後無効になる可能性があります。  
  
 クラスのクラスのコンス トラクターが完了したら、前に`GetRVAStaticAddress`は既に初期化することがいくつかの静的フィールドと、ガベージ コレクション オブジェクトをルートすることがありますが、すべての静的フィールドの CORPROF_E_DATAINCOMPLETE を返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
