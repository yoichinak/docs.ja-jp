---
title: CorGenericParamAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: bf0008ce9429671f0c156df4256bed0b2aaee184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176176"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr 列挙型
[:D ジェネリック](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)型の<xref:System.Type>パラメーターを記述する値を含みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`gpVarianceMask`|パラメーターの分散は、インターフェイスとデリゲートのジェネリック パラメーターにのみ適用されます。|  
|`gpNonVariant`|差異がないことを示します。|  
|`gpCovariant`|共分散を示します。|  
|`gpContravariant`|反変性を示します。|  
|`gpSpecialConstraintMask`|任意<xref:System.Type>のパラメータに特殊な制約を適用できます。|  
|`gpNoSpecialConstraint`|<xref:System.Type>パラメーターに制約が適用されなくなっています。|  
|`gpReferenceTypeConstraint`|パラメーターが<xref:System.Type>参照型である必要があることを示します。|  
|`gpNotNullableValueTypeConstraint`|パラメーターが<xref:System.Type>null 値にできない値型である必要があることを示します。|  
|`gpDefaultConstructorConstraint`|パラメーターにパラメーター<xref:System.Type>を受け取らない既定のパブリック コンストラクターが必要であることを示します。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コルドル.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
