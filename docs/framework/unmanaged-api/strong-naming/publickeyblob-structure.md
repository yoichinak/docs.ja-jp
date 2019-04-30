---
title: PublicKeyBlob 構造体
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a361e04b6f8f39ec0083471d8cb47d5a29376c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000351"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob 構造体
公開/秘密キーのペアの公開キーをバイナリ形式で表します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`SigAlgId`|署名アルゴリズムの識別子 (型の`ALG_ID`WinCrypt.h で定義されている、) の公開キー。|  
|`HashAlgId`|ハッシュ アルゴリズムの識別子 (型の`ALG_ID`WinCrypt.h で定義されている、) の公開キー。|  
|`cbPublicKey`|(バイト単位)、キーの長さ。|  
|`PublicKey`|CryptoAPI によって返される形式でキーの値を含む可変長バイト配列を指定します。|  
  
## <a name="remarks"></a>Remarks  
 `PublicKeyBlob`構造が使用者[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)、 [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)、および他の厳密な名前の関数を公開/秘密キーのペアの公開キーを表します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameGetPublicKey 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
