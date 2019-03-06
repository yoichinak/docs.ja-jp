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
ms.openlocfilehash: dac6f2ca813f3b8cbed48d540a991e6396edf679
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495222"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize 関数
厳密な名前の署名のサイズが返されます。 `StrongNameSignatureSize` 遅延署名アセンブリを作成するときに、ファイルに予約する領域の量を決定するコンパイラで通常に使用されます。  
  
 この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnamesignaturesize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a>パラメーター  
 `pbPublicKeyBlob`  
 [in]型の構造体[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)厳密な名前の署名を生成するためのキー ペアの公開部分を格納しています。  
  
 `cbPublicKeyBlob`  
 [in]サイズ (バイト単位) の`pbPublicKeyBlob`します。  
  
 `pcbSize`  
 [in]厳密な名前の署名を格納するために必要なバイト数。  
  
## <a name="return-value"></a>戻り値  
 `true` 正常に終了します。それ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 場合、`StrongNameSignatureSize`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [StrongNameSignatureSize メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
