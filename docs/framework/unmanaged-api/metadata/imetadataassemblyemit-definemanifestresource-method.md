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
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177871"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource メソッド
指定したマニフェスト リソースのメタデータを含む `ManifestResource` 構造体を作成し、関連付けられたメタデータ トークンを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [in]型`mdtFile`のメタデータ トークン、または`mdtAssemblyRef`リソース プロバイダーにマップされるメタデータ トークン。 NULL 値は、メタデータが埋め込まれているファイルがリソース プロバイダーであることを示します。  
  
 `dwOffset`  
 [in]ファイル内のリソースの先頭へのオフセット。 スタンドアロン ファイルのリソースの場合、これは常に 0 になります。 リソースが PE (ポータブル実行可能ファイル) ファイルに埋め込まれている場合、これは cor.h ヘッダー ファイルで指定された場所から開始されるリソース BLOB のオフセットです。  
  
 `dwResourceFlags`  
 [in]リソース定義のプロパティ設定を指定するフラグ値のビットごとの組み合わせ。  
  
 `pmdmr`  
 [アウト]返されたメタデータ トークンへのポインター。  
  
## <a name="remarks"></a>解説  
 アセンブリ`ManifestResource`のファイルごとに実装されるリソースごとに、1 つのメタデータ構造を定義する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[「システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
