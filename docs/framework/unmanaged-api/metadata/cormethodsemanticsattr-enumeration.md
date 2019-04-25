---
title: CorMethodSemanticsAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e36cb91c3ef741badb04b54e2b62158ecf6ced1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134499"
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr 列挙型
メソッドとそれに関連付けられているプロパティまたはイベントとの関係を記述する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`msSetter`|メソッドを指定します、`set`プロパティのアクセサー。|  
|`msGetter`|メソッドを指定します、`get`プロパティのアクセサー。|  
|`msOther`|メソッドに、プロパティまたはここで定義されているもの以外のイベントへのリレーションシップを指定します。|  
|`msAddOn`|メソッドがイベント ハンドラー メソッドを追加指定します。|  
|`msRemoveOn`|メソッドがイベント ハンドラー メソッドを削除するを指定します。|  
|`msFire`|メソッドがイベントを発生させることを指定します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
