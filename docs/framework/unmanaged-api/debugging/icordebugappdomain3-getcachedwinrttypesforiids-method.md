---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed1d7ad95b7c8474121994d0f54557c1c36cb531
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095127"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs メソッド
キャッシュされた列挙子を取得[!INCLUDE[wrt](../../../../includes/wrt-md.md)]アプリケーション ドメイン内の型、インターフェイスの id に基づいています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cReqTypes`  
 [in]必要な種類の数。  
  
 `iidsToResolve`  
 [in]マネージ表現に対応するインターフェイスの識別子を含む配列へのポインター、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]を取得する型。  
  
 `ppTypesEnum`  
 [out]キャッシュの列挙を許可する"ICorDebugTypeEnum"インターフェイス オブジェクトのアドレスへのポインターの表現の管理、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]インターフェイス識別子に基づいて、型が取得`iidsToResolve`します。  
  
## <a name="remarks"></a>Remarks  
 "ICorDebugTypeEnum"コレクション内の対応するエントリの種類には、メソッドは、特定のインターフェイスの識別子の情報を取得する失敗した場合、`ELEMENT_TYPE_END`のデータの取得に問題に起因するエラーまたは`ELEMENT_TYPE_VOID`不明なインターフェイス識別子。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugAppDomain3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
