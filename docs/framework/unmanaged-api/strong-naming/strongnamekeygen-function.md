---
title: StrongNameKeyGen 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8ebecce4078ba6c2b59e6bfba2d54300ba0c4ee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107381"
---
# <a name="strongnamekeygen-function"></a>StrongNameKeyGen 関数
厳密な名前を使用するために新しい公開/秘密キーの組が作成されます。  
  
 この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszKeyContainer`  
 [in]要求されたキー コンテナーの名前。 `wszKeyContainer` 空でない文字列であるか、一時テーブル名を生成する場合は null が必要です。  
  
 `dwFlags`  
 [in]登録されているキーのままにするかどうかを指定します。 次の値がサポートされています。  
  
-   0x00000000 の際に使用される`wszKeyContainer`一時的なキー コンテナーの名前を生成する場合は null です。  
  
-   0x00000001 (`SN_LEAVE_KEY`) のキーを左に登録する必要がありますを指定します。  
  
 `ppbKeyBlob`  
 [out]返された公開/秘密キー ペア。  
  
 `pcbKeyBlob`  
 [out]サイズ (バイト単位) の`ppbKeyBlob`します。  
  
## <a name="return-value"></a>戻り値  
 `true` 正常に終了します。それ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 `StrongNameKeyGen`関数は、1024 ビットのキーを作成します。 呼び出す必要があります、キーが取得された後、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)割り当てられたメモリを解放する関数。  
  
 場合、`StrongNameKeyGen`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameKeyGen メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [StrongNameKeyGenEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
