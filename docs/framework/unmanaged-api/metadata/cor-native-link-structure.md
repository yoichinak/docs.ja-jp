---
title: COR_NATIVE_LINK 構造体
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 812b70a594b5aa933f52d36f32d96d712267ecf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177956"
---
# <a name="cor_native_link-structure"></a>COR_NATIVE_LINK 構造体
ネイティブ コードのリンクに使用される情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`m_linkType`|ネイティブ コードでリンクされる型。 この値は、[いずれかの](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)値です。|  
|`m_flags`|ネイティブ コードをリンクするときにリンカーによって使用されるフラグ。 この値は、[いずれかの](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)値です。|  
|`m_entryPoint`|エントリ ポイントを表す MemberRef メタデータ トークン。 形式は `lib:entrypoint` です。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ構造体](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [CorNativeLinkType 列挙型](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [CorNativeLinkFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
