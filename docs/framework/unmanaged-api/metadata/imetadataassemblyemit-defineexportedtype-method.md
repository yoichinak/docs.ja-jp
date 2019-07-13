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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b4d143d8dd5391283736d0140e8f1ced1dec53e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775325"
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
 [in]エクスポートする型の名前。 エクスポートされた型の名前、共通言語ランタイムのバージョン 1.1 で指定された名前と一致する必要がありますの`TypeDef`型。  
  
 `tkImplementation`  
 [in]エクスポートされる型が実装されているを指定するトークンです。 有効な値とその意味は。  
  
- `mdFile` 種類は、このアセンブリ内の別のファイルに実装されます。  
  
- `mdAssemblyRef` 種類は、別のアセンブリに実装されます。  
  
- `mdExportedTYpe` 型が他の何らかの種類内で入れ子になった。  
  
- `mdFileNil` 種類は、マニフェストと同じファイルであり、入れ子になった型ではありません。  
  
 `tkTypeDef`  
 [in]エクスポートする型を指定するメタデータ トークンです。 この値が入力される、`TypeDef`内の型を実装、そのファイルがこのアセンブリ内にある場合にのみ関連するファイル内のテーブル。  
  
 `dwExportedTypeFlags`  
 [in]ビットごとの組み合わせ[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)エクスポートされる型のプロパティの設定を定義する列挙値。  
  
 `pmdct`  
 [out]エクスポートされた型を示す、返されたメタデータ トークンへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `ExportedType`このアセンブリによって公開されると、モジュール マニフェストを含む 1 つ以外で実装される各型のメタデータ構造を定義する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
