---
title: GUID_ManagedName 属性
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 110d6eb0abcf4b4ce73f1ee9d27e27122f360270
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374439"
---
# <a name="guid_managedname-attribute"></a>GUID_ManagedName 属性
コンポーネントオブジェクトモデル (COM) ライブラリのマネージ名前空間名を指定するカスタムインターフェイス属性を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>パラメーター  
 `value`  
 ライブラリのマネージ名前空間の名前。  
  
## <a name="definition"></a>定義  
 `GUID_ManagedName`は、Cor で次のように定義されています。  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Remarks  
 カスタムインターフェイス属性は、タイプライブラリ内のオブジェクトのメタデータを定義します。  
  
 属性<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType>から<xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType>マネージ名を取得するには、またはを使用します。  
  
 詳細については、ビジュアルC++リファレンスドキュメントの「[インターフェイス属性](/cpp/windows/attributes/interface-attributes)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、 `GUID_ManagedName`属性を使用したライブラリ定義を示しています。  
  
```  
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** Cor
