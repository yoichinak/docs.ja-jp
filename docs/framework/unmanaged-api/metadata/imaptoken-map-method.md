---
title: IMapToken::Map メソッド
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: fd362beb9f8fd7a1f2076eb6490a96c0358520e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432152"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map メソッド
Maps a relationship between the assemblies using metadata signatures.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tkImp`  
 [in] The metadata token that represents the imported code object.  
  
 `tkEmit`  
 [in] The metadata token that represents the emitted code object.  
  
## <a name="remarks"></a>Remarks  
 When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMapToken インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
