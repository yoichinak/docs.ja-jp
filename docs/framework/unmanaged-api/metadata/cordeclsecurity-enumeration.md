---
title: CorDeclSecurity 列挙型
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5409d1b89ba3e50c4ae17ed5aa6bf063cf6c93cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136969"
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity 列挙型
宣言型セキュリティを使用して実行できるセキュリティ アクションを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`dclActionMask`|予約済み。|  
|`dclActionNil`|予約済み。|  
|`dclRequest`|予約済み。|  
|`dclDemand`|呼び出し履歴の上位にあるすべての呼び出し元には、現在のアクセス許可オブジェクトで指定されたアクセス許可が付与されている必要があります。|  
|`dclAssert`|呼び出し元のコードは、リソースにアクセスするためのアクセス許可が呼び出し元のスタックの上位に与えられていない場合でも、現在のアクセス許可オブジェクトで識別されるリソースにアクセスできます。|  
|`dclDeny`|アクセス許可を付与されている場合でも、呼び出し元に対して、現在のアクセス許可オブジェクトによって指定されるリソースにアクセスする権限が拒否されました。|  
|`dclPermitOnly`|他のリソースにアクセスできるアクセス許可がコードに付与されていても、このアクセス許可オブジェクトで指定されたリソースにしかアクセスできません。|  
|`dclLinktimeCheck`|直前の呼び出し元は、一定の期間の指定した権限が付与されている必要があります。|  
|`dclInheritanceCheck`|別のクラスを継承またはメソッドをオーバーライドする派生クラスは、指定した権限が付与されている必要があります。|  
|`dclRequestMinimum`|呼び出し元は、コードを実行するために必要な最小限のアクセス許可を要求できます。 この操作は、アセンブリのスコープ内でのみ使用できます。|  
|`dclRequestOptional`|呼び出し元は、追加は省略可能です (実行には必要ありません) のアクセス許可を要求できます。 この要求は、個別に要求されていない、他のすべてのアクセス許可を暗黙的に拒否します。 この操作は、アセンブリのスコープ内でのみ使用できます。|  
|`dclRequestRefuse`|呼び出し元の要求が悪用された場合のアクセス許可は付与されません。 この操作は、アセンブリのスコープ内でのみ使用できます。|  
|`dclPrejitGrant`|予約済み。|  
|`dclPrejitDenied`|予約済み。|  
|`dclNonCasDemand`|予約済み。|  
|`dclNonCasLinkDemand`|直接の呼び出し元には、指定したアクセス許可が付与されている必要があります。|  
|`dclNonCasInheritance`|予約済み。|  
|`dclLinkDemandChoice`|予約済み。|  
|`dclInheritanceDemandChoice`|予約済み。|  
|`dclDemandChoice`|予約済み。|  
|`dclMaximumValue`|予約済み。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
