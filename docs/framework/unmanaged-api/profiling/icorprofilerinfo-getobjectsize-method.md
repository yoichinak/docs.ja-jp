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
ms.openlocfilehash: 2ad2092c902b137df0dfe108743ef4081ca5f04d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948113"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize メソッド
指定したオブジェクトのサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>パラメーター  
 `objectId`  
 からオブジェクトの ID です。  
  
 `pcSize`  
 入出力オブジェクトのサイズへのポインター (バイト単位)。  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]
> このメソッドは、互換性のために残されています。 64ビットプラットフォームで 4 GB を超えるオブジェクトの COR_E_OVERFLOW を返します。 代わりに[ICorProfilerInfo4:: GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)メソッドを使用してください。  
  
 多くの場合、同じ種類の異なるオブジェクトのサイズは同じです。 ただし、配列や文字列など、一部の型では、オブジェクトごとにサイズが異なる場合があります。  
  
 `GetObjectSize`メソッドによって返されるサイズには、オブジェクトがガベージコレクションヒープに配置された後に表示されるアラインメントの埋め込みは含まれません。 `GetObjectSize`メソッドを使用してオブジェクトからガベージコレクションヒープ上のオブジェクトに進む場合は、必要に応じて、手動でアラインメントのパディングを追加します。  
  
- 32ビット Windows、COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1、および COR_PRF_GC_GEN_2 では、4バイトのアラインメントが使用され、COR_PRF_GC_LARGE_OBJECT_HEAP では8バイトのアラインメントが使用されます。  
  
- 64ビットの Windows では、アラインメントは常に8バイトです。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Corprof.idl、Corprof.idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
