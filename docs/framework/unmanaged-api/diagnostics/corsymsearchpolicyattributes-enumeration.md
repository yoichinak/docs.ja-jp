---
title: CorSymSearchPolicyAttributes 列挙体
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: 786e53d43ecde0bc3a97fadb77184d25d41430bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178349"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes 列挙体
シンボル リーダーの検索を実行するときに使用するポリシーを指定します。 これらの定数は、[メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)によって使用されます。 [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)  
  
> [!IMPORTANT]
> 信頼できないソースからプログラム データベース (PDB) ファイルを開くと、セキュリティ上のリスクがあります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`AllowRegistryAccess`|レジストリにシンボル検索パスを照会します。|  
|`AllowSymbolServerAccess`|シンボル サーバーにアクセスします。|  
|`AllowOriginalPathAccess`|Debug ディレクトリで指定されたパスを検索します。|  
|`AllowReferencePathAccess`|.exe ファイルがある場所で PDB を検索します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** コーシム.idl,コーシム.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断列挙体](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
