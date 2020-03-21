---
title: ICorDebugProcess5::EnumerateGCReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178622"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>ICorDebugProcess5::EnumerateGCReferences メソッド
プロセスでガベージ コレクションされるすべてのオブジェクトの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `enumerateWeakReferences`  
 [in]弱い参照も列挙するかどうかを示すブール値。 の`enumerateWeakReferences``true`場合、`ppEnum`列挙子には厳密な参照と弱い参照の両方が含まれます。 の`enumerateWeakReferences`場合`false`、列挙子には厳密な参照のみが含まれます。  
  
 `ppEnum`  
 [アウト]ガベージ コレクションされるオブジェクトの列挙子である[ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)のアドレスへのポインター。  
  
## <a name="remarks"></a>解説  
 このメソッドは、プロセス内の任意のマネージ オブジェクトの完全なルート チェーンを決定する方法を提供し、オブジェクトがまだ生きている理由を判断するために使用できます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](icordebugprocess5-interface.md)
- [デバッグ インターフェイス](debugging-interfaces.md)
