---
title: ICorProfilerInfo2::GetStringLayout メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfa6f5cb5aae2124f04580ce49064ba857e2602
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473033"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout メソッド
文字列オブジェクトのレイアウトに関する情報を取得します。 このメソッドは非推奨、 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]、優先されると、 [icorprofilerinfo 3::getstringlayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pBufferLengthOffset`  
 [out]相対の場所のオフセットへのポインター、`ObjectID`ポインターは、文字列の長さを格納します。 長さが格納されている、`DWORD`します。  
  
> [!NOTE]
>  このパラメーターは、バッファーの長さではなく、文字列、自体の長さを返します。 バッファーの長さは使用できなくします。  
  
 `PStringLengthOffset`  
 [out]相対の場所のオフセットへのポインター、`ObjectID`文字列自体の長さを格納するポインター。 長さが格納されている、`DWORD`します。  
  
 `pBufferOffset`  
 [out]バッファーの相対オフセットへのポインター、 `ObjectID` 、ワイド文字の文字列を格納するポインター。  
  
## <a name="remarks"></a>Remarks  
 `GetStringLayout`メソッドに関連する、オフセットを取得する、`ObjectID`ポインターは、次が格納されている場所の。  
  
-   文字列のバッファーの長さ。  
  
-   文字列自体の長さ。  
  
-   ワイド文字の実際の文字列を格納するバッファー。  
  
 文字列には、null で終わる可能性があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
