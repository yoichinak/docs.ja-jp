---
title: ICLRMetadataLocator::GetMetadata メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74a54da0bc4257ccc50d2d99177a17b796380fb3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481431"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata メソッド
イメージのメタデータを取得する共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `imagePath`  
 [in]イメージ ファイルのパスを指定する文字列。  
  
 `imageTimestamp`  
 [in]イメージ ファイルのタイムスタンプ。  
  
 `imageSize`  
 [in]イメージ ファイルのサイズ。  
  
 `mvid`  
 [in]イメージのグローバルに一意の識別子。  
  
 `mdRva`  
 [in]メタデータの相対仮想アドレス (RVA)。 アドレスは、イメージのベース アドレスに対して相対的です。  
  
 `flags`  
 [in]将来使用するために予約されています。  
  
 `bufferSize`  
 [in]メタデータの配置先となるバッファーのサイズ。  
  
 `buffer`  
 [out]メタデータの配置先となるバッファー。  
  
 `dataSize`  
 [out]返されるメタデータのサイズ。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICLRMetadataLocator インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
