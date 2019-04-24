---
title: CorFieldAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 432e202eb8db105e8d56d3d36cdc8001bac5320c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182378"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr 列挙型
フィールドについてのメタデータを記述する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`fdFieldAccessMask`|アクセシビリティに関する情報を指定します。|  
|`fdPrivateScope`|フィールドを参照できないことを指定します。|  
|`fdPrivate`|フィールドが親の型からのみアクセスできることを指定します。|  
|`fdFamANDAssem`|フィールドにそのアセンブリの派生クラスからアクセスできることを指定します。|  
|`fdAssembly`|フィールドにそのアセンブリ内のすべての型からアクセスできることを指定します。|  
|`fdFamily`|フィールドの型によってのみアクセスできますが、派生クラスを指定します。|  
|`fdFamORAssem`|フィールドにそのアセンブリ内のすべての型と派生クラスによってアクセスできることを指定します。|  
|`fdPublic`|フィールドがこのスコープの可視性を持つすべての種類でアクセスできることを指定します。|  
|`fdStatic`|フィールドがインスタンス メンバーではなく、その型のメンバーであるを指定します。|  
|`fdInitOnly`|初期化された後に、フィールドを変更できないことを指定します。|  
|`fdLiteral`|フィールド値がコンパイル時定数であることを指定します。|  
|`fdNotSerialized`|その型は、リモート処理は実行時にフィールドはシリアルされないことを指定します。|  
|`fdSpecialName`|フィールドに、特別なことと、その名前を記述しているを指定しますか。|  
|`fdPinvokeImpl`|フィールドの実装が PInvoke 経由で転送されることを指定します。|  
|`fdReservedMask`|共通言語ランタイムでは、内部使用のため予約されています。|  
|`fdRTSpecialName`|共通言語ランタイム メタデータの内部 Api が名前のエンコーディングを確認する必要がありますように指定します。|  
|`fdHasFieldMarshal`|フィールドにマーシャ リング情報が含まれることを指定します。|  
|`fdHasDefault`|フィールドが既定値を持つことを指定します。|  
|`fdHasFieldRVA`|フィールドの相対仮想アドレスを持つことを指定します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
