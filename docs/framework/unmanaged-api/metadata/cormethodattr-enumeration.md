---
title: CorMethodAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 249de91483117db6b497fa8eae6f97c3eb0a0587
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176996"
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr 列挙型
メソッドの機能を記述する値が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`mdMemberAccessMask`|メンバーへのアクセスを指定します。|  
|`mdPrivateScope`|メンバーを参照できないことを指定します。|  
|`mdPrivate`|メンバーが親の型からのみアクセスできることを指定します。|  
|`mdFamANDAssem`|メンバーがこのアセンブリでのみサブタイプ アクセスできることを指定します。|  
|`mdAssem`|メンバーがアクセスできます。 アセンブリ内のすべてのユーザーがあることを指定します。|  
|`mdFamily`|メンバーが型とサブタイプによってのみアクセスできることを指定します。|  
|`mdFamORAssem`|メンバーがアクセスできるは、そのアセンブリ内の他の型と派生クラスであることを指定します。|  
|`mdPublic`|メンバーがスコープにアクセスできるアクセス権を持つすべての種類であることを指定します。|  
|`mdStatic`|インスタンスのメンバーではなく、型の一部として、メンバーが定義されていることを指定します。|  
|`mdFinal`|メソッドをオーバーライドできないことを指定します。|  
|`mdVirtual`|メソッドをオーバーライドできることを指定します。|  
|`mdHideBySig`|メソッドには、名前だけではなく、名前とシグネチャで非表示にするを指定します。|  
|`mdVtableLayoutMask`|仮想テーブルのレイアウトを指定します。|  
|`mdReuseSlot`|仮想テーブルでは、このメソッドの使用、スロットが再利用することを指定します。 既定値です。|  
|`mdNewSlot`|メソッドは、仮想テーブルの新しいスロットを常に取得を指定します。|  
|`mdCheckAccessOnOverride`|表示は同じ型でメソッドをオーバーライドできることを指定します。|  
|`mdAbstract`|メソッドが実装されていないことを指定します。|  
|`mdSpecialName`|メソッドが、特別なと、その名前を記述しているを指定する方法。|  
|`mdPinvokeImpl`|メソッドの実装が PInvoke を使用して転送されることを指定します。|  
|`mdUnmanagedExport`|メソッドがアンマネージ コードにエクスポートする管理対象のメソッドを指定します。|  
|`mdReservedMask`|共通言語ランタイムでは、内部使用のため予約されています。|  
|`mdRTSpecialName`|共通言語ランタイムがメソッド名のエンコードを確認する必要がありますように指定します。|  
|`mdHasSecurity`|メソッドに関連付けられているセキュリティを指定します。|  
|`mdRequireSecObject`|メソッドがセキュリティ コードを含む他のメソッドを呼び出すことを指定します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
