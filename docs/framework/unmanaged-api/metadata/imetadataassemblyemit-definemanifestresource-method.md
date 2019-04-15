---
title: IMetaDataAssemblyEmit::DefineManifestResource メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b617e29e2df22b59114c8b978daa645de1cc6176
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186720"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource メソッド
指定したマニフェスト リソースのメタデータを含む `ManifestResource` 構造体を作成し、関連付けられたメタデータ トークンを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szName`  
 [in]リソースの名前。  
  
 `tkImplementation`  
 [in]型のメタデータ トークン`mdtFile`または`mdtAssemblyRef`リソース プロバイダーにマップされます。 NULL 値は、メタデータが埋め込まれているファイルがリソース プロバイダーであることを示します。  
  
 `dwOffset`  
 [in]リソース ファイル内の先頭までのオフセット。 スタンドアロン ファイル内のリソース、0 はこれが常にします。 PE (移植可能な実行可能ファイル) ファイルには、リソースが埋め込まれている場合は cor.h ヘッダー ファイルで指定された場所から始まる、BLOB リソースのオフセットです。  
  
 `dwResourceFlags`  
 [in]リソース定義のプロパティの設定を指定するフラグ値のビットごとの組み合わせ。  
  
 `pmdmr`  
 [out]返されるメタデータ トークンへのポインター。  
  
## <a name="remarks"></a>Remarks  
 1 つ`ManifestResource`の各アセンブリのファイルに実装されている各リソースのメタデータ構造を定義する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
