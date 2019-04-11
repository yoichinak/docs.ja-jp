---
title: ICorProfilerInfo::GetObjectSize メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d366a0093ca82d2e5b3c40729777a1b6c0766bda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092202"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize メソッド
指定したオブジェクトのサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>パラメーター  
 `objectId`  
 [in]オブジェクトの ID。  
  
 `pcSize`  
 [out]オブジェクトのサイズ (バイト) へのポインター。  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]
>  このメソッドは、互換性のために残されています。 返されます COR_E_OVERFLOW オブジェクト 4 GB より大きい 64 ビット プラットフォームで。 使用して、 [icorprofilerinfo 4::getobjectsize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)メソッド代わりにします。  
  
 多くの場合、同じ種類の異なるオブジェクトと同じサイズである場合します。 ただし、配列や文字列など、一部の種類には、オブジェクトごとに別のサイズがあります。  
  
 によって返されるサイズ、`GetObjectSize`メソッドにオブジェクトがガベージ コレクション ヒープに後に表示される配置の埋め込みは含まれません。 使用する場合、`GetObjectSize`オブジェクトからオブジェクトをガベージ コレクション ヒープで切り替わるようにメソッドが配置を手動で、必要に応じてパディングを追加します。  
  
-   32 ビットの Windows では、COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1、および COR_PRF_GC_GEN_2 4 バイトのアラインメントを使用して、COR_PRF_GC_LARGE_OBJECT_HEAP が 8 バイト アラインメントを使用します。  
  
-   64 ビットの Windows では、配置と、8 バイトでは常にします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
