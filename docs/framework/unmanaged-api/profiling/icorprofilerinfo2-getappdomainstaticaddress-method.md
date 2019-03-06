---
title: ICorProfilerInfo2::GetAppDomainStaticAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e2b4ec0183f010cfc9ad4fce21cf0f616b0ef3c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472461"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a>ICorProfilerInfo2::GetAppDomainStaticAddress メソッド
指定したアプリケーション ドメインのスコープ内の指定されたアプリケーション ドメインの静的フィールドのアドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>パラメーター  
 `classId`  
 [in]要求されたアプリケーション ドメインの静的フィールドを格納するクラスのクラス ID。  
  
 `fieldToken`  
 [in]要求されたアプリケーション ドメインの静的フィールドのメタデータ トークンです。  
  
 `appDomainId`  
 [in]要求された静的フィールドのスコープとなっているアプリケーション ドメインの ID。  
  
 `ppAddress`  
 [out]指定したアプリケーション ドメイン内にある静的フィールドのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `GetAppDomainStaticAddress`メソッドは、次のいずれかを返す可能性があります。  
  
-   指定された静的フィールドに指定したコンテキスト内のアドレスが割り当てられていない場合の CORPROF_E_DATAINCOMPLETE HRESULT。  
  
-   ガベージ コレクション ヒープで可能性のあるオブジェクトのアドレス。 これらのアドレスは、ガベージ コレクション後にプロファイラーを想定しないでくださいが有効であるために、ガベージ コレクションの後無効になる可能性があります。  
  
 クラスのクラスのコンス トラクターが完了したら、前に`GetAppDomainStaticAddress`はいくつかの静的フィールドは既に初期化可能性がありますが、すべての静的フィールドの CORPROF_E_DATAINCOMPLETE を返し、ガベージ コレクション オブジェクトのルートします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
