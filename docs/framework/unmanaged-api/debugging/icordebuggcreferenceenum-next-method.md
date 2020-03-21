---
title: ICorDebugGCReferenceEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: d87f414e9dfd05a519b60efc7ecdd5328a6dd86f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178867"
---
# <a name="icordebuggcreferenceenumnext-method"></a>ICorDebugGCReferenceEnum::Next メソッド
ガベージ コレクションされるオブジェクトに関する情報を含む、指定した数の[COR_GC_REFERENCE](cor-gc-reference-structure.md)インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 celt  
 [in]取得するルートの数。  
  
 根  
 [アウト]ガベージ コレクションされるオブジェクトのルートを表す[COR_GC_REFERENCE](cor-gc-reference-structure.md)オブジェクトを指すポインターの配列。  
  
 pceltFetched  
 [アウト]で実際に返される[COR_GC_REFERENCE](cor-gc-reference-structure.md)オブジェクトの数へのポインター `roots`。 `celt` が 1 の場合、この値は`null` になることがあります。  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugGCReferenceEnum インターフェイス](icordebuggcreferenceenum-interface.md)
- [デバッグ インターフェイス](debugging-interfaces.md)
