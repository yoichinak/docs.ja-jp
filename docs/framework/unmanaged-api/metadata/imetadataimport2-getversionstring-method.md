---
title: IMetaDataImport2::GetVersionString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a01b4203145f6ffee4e3a11a3526f0b83e3dc741
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154623"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString メソッド
アセンブリのビルドに使用されたランタイムのバージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzBuf`  
 [out]バージョンを指定する文字列を格納する配列。  
  
 `ccBufSize`  
 [in]ワイド文字単位のサイズの`pwzBuf`配列。  
  
 `pccBufSize`  
 [out]返される、null 終端文字を含め、ワイド文字の数、`pwzBuf`配列。  
  
## <a name="remarks"></a>Remarks  
 `GetVersionString`メソッドは、現在のメタデータ スコープのビルドのバージョンを取得します。 スコープが保存されていないこと、ビルドのバージョンはありませんし、空の文字列が返されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
