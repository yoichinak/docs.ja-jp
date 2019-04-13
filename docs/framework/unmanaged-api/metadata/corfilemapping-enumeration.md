---
title: CorFileMapping 列挙体
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3056836d289383161f9fa538c3c6349f88b6ba6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175618"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping 列挙体
呼び出しから返されるファイル マッピングの種類を記述する値が含まれています、 [imetadatainfo::getfilemapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`fmFlat`|ファイルは、データ ファイルとしてマップされます。 つまり、`SEC_IMAGE`フラグは、Microsoft Win32 に渡されなかった`CreateFileMapping`関数。|  
|`fmExecutableImage`|いずれかを使用して、実行するため、ファイルがマップされている、`LoadLibrary`関数または`CreateFileMapping`関数と、`SEC_IMAGE`フラグ。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [GetFileMapping メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
