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
ms.openlocfilehash: 51741aa3a6d965c1e9743081628d8ad62e8fb04e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176202"
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
|`catAssembly`|アセンブリに属性を適用できます。|  
|`catModule`|属性は、ポータブル実行可能 (.dll または .exe) モジュールに適用できます。|  
|`catClass`|クラスに属性を適用できます。|  
|`catStruct`|構造体、つまり、値型に属性を適用できます。|  
|`catEnum`|列挙体に属性を適用できます。|  
|`catConstructor`|コンストラクターに属性を適用できます。|  
|`catMethod`|メソッドに属性を適用できます。|  
|`catProperty`|プロパティに属性を適用できます。|  
|`catField`|フィールドに属性を適用できます。|  
|`catEvent`|イベントに属性を適用できます。|  
|`catInterface`|インターフェイスに属性を適用できます。|  
|`catParameter`|パラメーターに属性を適用できます。|  
|`catDelegate`|デリゲートに属性を適用できます。|  
|`catGenericParameter`|ジェネリック パラメーターに属性を適用できます。|  
|`catAll`|任意のアプリケーション要素に属性を適用できます。|  
|`catClassMembers`|属性はクラスのメンバーに適用できます。|  
  
## <a name="remarks"></a>解説  
 列挙`CorAttributeTargets`値をビットごとの OR 演算と組み合わせて、優先する組み合わせを取得できます。  
  
 マネージ`CorAttributeTargets`<xref:System.AttributeTargets?displayProperty=nameWithType>列挙体と並列処理を行います。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コルドル.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
