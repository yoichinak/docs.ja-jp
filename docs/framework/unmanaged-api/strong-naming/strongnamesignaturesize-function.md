---
title: StrongNameSignatureSize 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f98b971e430a2c35a4c484f4f9c4bf387c640c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798955"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize 関数
厳密な名前の署名のサイズが返されます。 `StrongNameSignatureSize`は、通常、コンパイラによって使用され、遅延署名されたアセンブリを作成するときにファイルで予約する領域の量を決定します。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a>パラメーター  
 `pbPublicKeyBlob`  
 から厳密な名前の署名を生成するために使用されるキーペアの公開部分を格納する[Publickeyblob](publickeyblob-structure.md)型の構造体。  
  
 `cbPublicKeyBlob`  
 からの`pbPublicKeyBlob`サイズ (バイト単位)。  
  
 `pcbSize`  
 から厳密な名前の署名を格納するために必要なバイト数。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に完了した場合は。それ以外`false`の場合は。  
  
## <a name="remarks"></a>Remarks  
 関数が正常に完了しない場合は、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。`StrongNameSignatureSize`  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureSize メソッド](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
