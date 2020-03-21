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
ms.openlocfilehash: 2f9325f3795262a0c33af02f87fc5d3a020658cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177641"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope メソッド
新しいメタデータを作成できる領域をメモリ内に作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `rclsid`  
 [in]作成するメタデータ構造のバージョンの CLSID。 この値は、.NET Framework バージョン 2.0 のCLSID_CorMetaDataRuntimeする必要があります。  
  
 `dwCreateFlags`  
 [in]オプションを指定するフラグ。 この値は、.NET Framework 2.0 の場合は 0 である必要があります。  
  
 `riid`  
 [in]返される必要なメタデータ インターフェイスの IID。呼び出し元は、インターフェイスを使用して新しいメタデータを作成します。  
  
 の値は`riid`、"emit"インタフェースの1つを指定する必要があります。 有効な値は、IID_IMetaDataEmit、IID_IMetaDataAssemblyEmit、またはIID_IMetaDataEmit2です。  
  
 `ppIUnk`  
 [アウト]返されたインターフェイスへのポインター。  
  
## <a name="remarks"></a>解説  
 `DefineScope`インメモリ メタデータ テーブルのセットを作成し、メタデータの一意の GUID (モジュール バージョン識別子、または MVID) を生成し、生成されるコンパイル 単位のモジュール テーブルにエントリを作成します。  
  
 必要に応じて[、IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)または[IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)メソッドを使用して、メタデータ スコープ全体に属性をアタッチできます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[「システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
