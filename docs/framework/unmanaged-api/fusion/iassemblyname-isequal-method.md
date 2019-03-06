---
title: IAssemblyName::IsEqual メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cae8f326a293a40164120dc17c13e451c4e93f1f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489437"
---
# <a name="iassemblynameisequal-method"></a>IAssemblyName::IsEqual メソッド
指定したかどうかを判断します[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)オブジェクトがこれと等しい`IAssemblyName`を基に、指定した比較フラグ。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pName`  
 [in]`IAssemblyName`これと比較するオブジェクト`IAssemblyName`します。  
  
 `dwCmpFlags`  
 [in]ビットごとの組み合わせ[ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)比較に影響を与える値。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IAssemblyName インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [Fusion 列挙型](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
