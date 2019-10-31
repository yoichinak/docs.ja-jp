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
ms.openlocfilehash: 0369cc6d98736542b764e5914d733a9341753b24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088882"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs メソッド
インターフェイス識別子に基づいて、アプリケーションドメイン内のキャッシュされた Windows ランタイム型の列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cReqTypes`  
 から要求される型の数。  
  
 `iidsToResolve`  
 から取得する Windows ランタイム型のマネージ表現に対応するインターフェイス識別子を格納する配列へのポインター。  
  
 `ppTypesEnum`  
 入出力`iidsToResolve`のインターフェイス識別子に基づいて、取得された Windows ランタイム型のキャッシュされたマネージ表現を列挙できるようにする、"" "の" "ツール" インターフェイスオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 メソッドが特定のインターフェイス識別子に関する情報の取得に失敗した場合、データの取得に関する問題が原因でエラーが発生した場合、または不明なインターフェイス識別子の `ELEMENT_TYPE_VOID` については、"" の種類 "というコレクション内の対応するエントリの `ELEMENT_TYPE_END` 型になります。  
  
## <a name="requirements"></a>［要件］  
 **プラットフォーム:** Windows ランタイム  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugAppDomain3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
