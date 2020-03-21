---
title: IMetaDataAssemblyEmit::DefineExportedType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177877"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType メソッド
指定してエクスポートした型のメタデータが含まれる `ExportedType` 構造体を作成し、関連付けられたメタデータ トークンを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szName`  
 [in]エクスポートする型の名前。 共通言語ランタイムのバージョン 1.1 の場合、エクスポートされる型の名前は、型の で`TypeDef`指定された名前と完全に一致する必要があります。  
  
 `tkImplementation`  
 [in]エクスポートされた型が実装される場所を指定するトークン。 有効な値と、関連する意味は次のとおりです。  
  
- `mdFile`型は、このアセンブリ内の別のファイルに実装されます。  
  
- `mdAssemblyRef`型は別のアセンブリに実装されています。  
  
- `mdExportedTYpe`型は他の型内で入れ子になります。  
  
- `mdFileNil`型はマニフェストと同じファイルにあり、入れ子になった型ではありません。  
  
 `tkTypeDef`  
 [in]エクスポートする型を指定するメタデータへのトークン。 この値は、型を`TypeDef`実装するファイルのテーブルに入力され、そのファイルがこのアセンブリ内にある場合にのみ関連します。  
  
 `dwExportedTypeFlags`  
 [in]エクスポートされた型のプロパティ設定を定義する[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)列挙値のビットごとの組み合わせ。  
  
 `pmdct`  
 [アウト]エクスポートされた型を示す、返されたメタデータ トークンへのポインター。  
  
## <a name="remarks"></a>解説  
 メタデータ`ExportedType`構造は、このアセンブリによって公開され、マニフェストを含むモジュール以外のモジュールに実装される型ごとに定義する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[「システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
