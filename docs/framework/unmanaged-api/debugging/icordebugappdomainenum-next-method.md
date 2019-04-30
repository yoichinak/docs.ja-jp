---
title: ICorDebugAppDomainEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fefc933cc84fede1f3dea16d4b13e09801a96e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996152"
---
# <a name="icordebugappdomainenumnext-method"></a>ICorDebugAppDomainEnum::Next メソッド
現在のカーソル位置から、コレクションから指定されたアプリケーション ドメイン数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `celt`  
 [in]取得するアプリケーション ドメインの数。  
  
 `values`  
 [out]アプリケーション ドメインを表す ICorDebugAppDomain オブジェクトを指す各ポインターの配列。  
  
 `pceltFetched`  
 [out]実際に返されるアプリケーション ドメインの数へのポインター。 この値は null になる場合`celt`は 1 つです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
