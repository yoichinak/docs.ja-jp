---
title: ICorProfilerInfo3::GetThreadStaticAddress2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f62dadf4f21022f8f425596cf5957891ed39effe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049506"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a>ICorProfilerInfo3::GetThreadStaticAddress2 メソッド
指定したスレッドおよびアプリケーション ドメインのスコープ内にある、指定したスレッド内静的フィールドのアドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>パラメーター  
 `classId`  
 [in]要求されたスレッド内静的フィールドを含むクラスの ID。  
  
 `fieldToken`  
 [in]要求されたスレッド内静的フィールドのメタデータ トークン。  
  
 `appDomainId`  
 [in] アプリケーション ドメインの ID。  
  
 `threadId`  
 [in]要求された静的フィールドのスコープにあるスレッドの ID。  
  
 `ppAddress`  
 [out]指定したスレッド内の静的フィールドのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `GetThreadStaticAddress2`メソッドは、次のいずれかを返す可能性があります。  
  
- 指定された静的フィールドに指定したコンテキスト内のアドレスが割り当てられていない場合の CORPROF_E_DATAINCOMPLETE HRESULT。  
  
- ガベージ コレクション ヒープで可能性のあるオブジェクトのアドレス。 これらのアドレスは、ガベージ コレクション後にプロファイラーを想定しないでくださいが有効であるために、ガベージ コレクションの後無効になる可能性があります。  
  
 クラスのクラスのコンス トラクターが完了したら、前に`GetThreadStaticAddress2`はいくつかの静的フィールドは既に初期化可能性がありますが、すべての静的フィールドの CORPROF_E_DATAINCOMPLETE を返し、ガベージ コレクション オブジェクトのルートします。  
  
 [Icorprofilerinfo 2::getthreadstaticaddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)メソッドは、`GetThreadStaticAddress2`メソッドがアプリケーション ドメインの引数は受け付けません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
