---
title: ICLRStrongName::GetHashFromAssemblyFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 714827da24b3fc0a334210fd94e61f80cb2afe49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993110"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a>ICLRStrongName::GetHashFromAssemblyFile メソッド
指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szFilePath`  
 [in]ハッシュされるファイルへのパス。  
  
 `piHashAlg`  
 [入力、出力]ハッシュ アルゴリズムを指定する定数。 既定のハッシュ アルゴリズムのゼロを使用します。  
  
 `pbHash`  
 [out]返されたハッシュ バッファー。  
  
 `cchHash`  
 [in]要求の最大サイズの`pbHash`します。  
  
 `pchHash`  
 [out]サイズ (バイト単位) が返されますの`pbHash`します。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` メソッドが正常に完了した場合それ以外の場合、エラーを示す HRESULT 値 (を参照してください[の共通 HRESULT 値](https://go.microsoft.com/fwlink/?LinkId=213878)一覧については)。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromAssemblyFileW メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
