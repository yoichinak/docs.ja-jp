---
title: CorPEKind 列挙型
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bfe30567bcd8e22a82d401e00b0a6ee50407def
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781668"
---
# <a name="corpekind-enumeration"></a>CorPEKind 列挙型
呼び出しから返される、ポータブル実行可能 (PE) ファイルを記述する値を含む[imetadataimport 2::getpekind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`peNot`|PE ファイルではないことを示します。|  
|`peILOnly`|この PE ファイルには、マネージ コードだけが含まれていることを示します。|  
|`pe32BitRequired`|この PE ファイルが Win32 呼び出しを行うことを示します。|  
|`pe32Plus`|64 ビット プラットフォームでこの PE ファイルを実行することを示します。|  
|`pe32Unmanaged`|この PE ファイルがネイティブ コードであることを示します。|  
|pe32BitPreferred|この PE ファイルが 32 ビット環境に読み込むことが推奨プラットフォームに依存しないことを示します。|  
  
## <a name="remarks"></a>Remarks  
 これらの値は、ビットごとの組み合わせで使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
