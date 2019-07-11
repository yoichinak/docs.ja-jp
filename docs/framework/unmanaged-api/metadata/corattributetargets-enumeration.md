---
title: CorAttributeTargets 列挙型
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9fb1dff80fccc920540d370797441b3a019d766c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780920"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets 列挙型
属性を適用できるアプリケーション要素を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =   
        catAssembly | catModule | catClass | catStruct |   
        catEnum | catConstructor | catMethod | catProperty |   
        catField | catEvent | catInterface | catParameter |   
        catDelegate | catGenericParameter,  
  
    catClassMembers        =   
        catClass | catStruct | catEnum | catConstructor |   
        catMethod | catProperty | catField | catEvent |   
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`catAssembly`|属性は、アセンブリに適用できます。|  
|`catModule`|属性は、ポータブル実行可能ファイル (.dll または .exe) モジュールに適用できます。|  
|`catClass`|属性は、クラスに適用できます。|  
|`catStruct`|構造体に属性を適用できます。つまり、値を入力します。|  
|`catEnum`|属性は、列挙体に適用できます。|  
|`catConstructor`|属性は、コンス トラクターに適用できます。|  
|`catMethod`|属性は、メソッドに適用できます。|  
|`catProperty`|属性は、プロパティに適用できます。|  
|`catField`|属性は、フィールドに適用できます。|  
|`catEvent`|属性は、イベントに適用できます。|  
|`catInterface`|属性は、インターフェイスに適用できます。|  
|`catParameter`|属性は、パラメーターに適用できます。|  
|`catDelegate`|属性は、デリゲートに適用できます。|  
|`catGenericParameter`|属性は、ジェネリック パラメーターに適用できます。|  
|`catAll`|属性は、任意のアプリケーション要素に適用できます。|  
|`catClassMembers`|属性は、クラスのメンバーに適用できます。|  
  
## <a name="remarks"></a>Remarks  
 `CorAttributeTargets`列挙値は、任意の組み合わせを取得するビットごとの OR 演算と組み合わせることができます。  
  
 `CorAttributeTargets`マネージ対応<xref:System.AttributeTargets?displayProperty=nameWithType>列挙体。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
