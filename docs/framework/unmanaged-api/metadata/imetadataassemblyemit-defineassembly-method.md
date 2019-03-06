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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf6e0c1de9bfb920932e5c22adb4eb8573125506
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489959"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly メソッド
作成、`Assembly`指定されたアセンブリのメタデータを含むを構造体し、関連付けられたメタデータ トークンを返します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]アセンブリの厳密に名前がない場合は、アセンブリ、または NULL の発行元を識別する公開キー。  
  
 `cbPublicKey`  
 [in]バイト サイズ`pbPublicKey`します。  
  
 `uHashAlgId`  
 [in]Sha-1 アルゴリズムを指定するには、アセンブリ、または NULL でファイルの暗号化に使用するハッシュ アルゴリズムの識別子。  
  
 `szName`  
 [in]アセンブリの人間が判読できるテキストの名前。 この値は 1024 文字を超えない必要があります。  
  
 `pMetaData`  
 [in]アセンブリのバージョン、プラットフォーム、およびロケール情報を含む ASSEMBLYMETADATA インスタンスへのポインター。  
  
 `dwAssemblyFlags`  
 [in]組み合わせた[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)アセンブリの機能を記述する値。  
  
 `pmda`  
 [out]メタデータ トークンへのポインター。  
  
## <a name="remarks"></a>Remarks  
 1 つだけ`Assembly`メタデータ構造体は、マニフェスト内で定義することができます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
