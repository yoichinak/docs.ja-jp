---
title: ICLRStrongName::GetHashFromFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f410e38d846969bbd23ff5b0a6751a5202088254
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771528"
---
# <a name="iclrstrongnamegethashfromfile-method"></a>ICLRStrongName::GetHashFromFile メソッド
指定したファイルの内容に対してハッシュが生成されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szFilePath`  
 [in]ハッシュするファイルの名前。  
  
 `piHashAlg`  
 [入力、出力]ハッシュを生成するときに使用するアルゴリズム。 有効なアルゴリズムを使用して、Win32 CryptoAPI で定義されています。 場合`piHashAlg`CALG_SHA 1 が使用される既定のアルゴリズムを 0 に設定されます。  
  
 `pbHash`  
 [out]生成されたハッシュを含むバイト配列。  
  
 `cchHash`  
 [in]バッファーの最大サイズを`pbHash`を指します。  
  
 `pchHash`  
 [out]サイズ (バイト単位)、返された`pbHash`します。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` メソッドが正常に完了した場合それ以外の場合、エラーを示す HRESULT 値 (を参照してください[の共通 HRESULT 値](https://go.microsoft.com/fwlink/?LinkId=213878)一覧については)。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは同じ、 [iclrstrongname::gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)メソッド、名前を指定する点を除いては Unicode ではなく ANSI です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromFileW メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
