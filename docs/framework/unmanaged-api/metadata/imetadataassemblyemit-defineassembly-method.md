---
title: IMetaDataAssemblyEmit::DefineAssembly メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177885"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly メソッド
指定した`Assembly`アセンブリのメタデータを含む構造体を作成し、関連付けられたメタデータ トークンを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbPublicKey`  
 [in]アセンブリの発行者を識別する公開キー。  
  
 `cbPublicKey`  
 [in]のサイズ (バイト`pbPublicKey`単位)  
  
 `uHashAlgId`  
 [in]アセンブリ内のファイルの暗号化に使用するハッシュ アルゴリズムの識別子。または NULL を使用して SHA-1 アルゴリズムを指定します。  
  
 `szName`  
 [in]アセンブリの人間が判読できるテキスト名。 この値は 1024 文字を超えることはできません。  
  
 `pMetaData`  
 [in]アセンブリのバージョン、プラットフォーム、およびロケール情報を含む ASSEMBLYMETADATA インスタンスへのポインター。  
  
 `dwAssemblyFlags`  
 [in]アセンブリの機能を記述する[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)値の組み合わせ。  
  
 `pmda`  
 [アウト]メタデータ トークンへのポインター。  
  
## <a name="remarks"></a>解説  
 マニフェスト内`Assembly`で定義できるメタデータ構造は 1 つだけです。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
