---
title: IMetaDataDispenser::DefineScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76a439effad9cb3f6dcdd232590cf2196ee7ab99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101407"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope メソッド
メモリの新しいメタデータを作成するには、新しい領域を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `rclsid`  
 [in]作成するメタデータ構造体のバージョンの CLSID。 この値は、.NET Framework version 2.0 の CLSID_CorMetaDataRuntime を指定する必要があります。  
  
 `dwCreateFlags`  
 [in]オプションを指定するフラグ。 この値は、.NET Framework 2.0 の 0 にする必要があります。  
  
 `riid`  
 [in]返される必要なメタデータ インターフェイスの IID呼び出し元はインターフェイスを使用して、新しいメタデータを作成します。  
  
 値`riid`「生成」インターフェイスのいずれかを指定する必要があります。 有効な値は IID_IMetaDataEmit、IID_IMetaDataAssemblyEmit、または IID_IMetaDataEmit2 です。  
  
 `ppIUnk`  
 [out]返されたインターフェイスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `DefineScope` メモリ内のメタデータ テーブルのセットを作成し、メタデータの一意の GUID (モジュールのバージョンの識別子、または MVID) が生成されますが生成するコンパイル単位の module テーブル エントリを作成します。  
  
 使用して、全体としてのメタデータ スコープの属性をアタッチすることができます、 [imetadataemit::setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)または[imetadataemit::definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)として適切なメソッドです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
