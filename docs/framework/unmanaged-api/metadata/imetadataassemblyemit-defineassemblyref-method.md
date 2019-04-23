---
title: IMetaDataAssemblyEmit::DefineAssemblyRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e480c408c10eb9e135f260426750f7747e5d8ce5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117353"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef メソッド
このアセンブリが参照するアセンブリのメタデータを含む `AssemblyRef` 構造体を作成し、関連付けられたメタデータ トークンを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbPublicKeyOrToken`  
 [in]参照先アセンブリの発行者の公開キー。 ヘルパー関数[StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)このパラメーターとして渡すパブリック キーのハッシュを取得するために使用できます。  
  
 `cbPublicKeyOrToken`  
 [in]バイト サイズ`pbPublicKeyOrToken`します。  
  
 `szName`  
 [in]アセンブリの人間が判読できるテキストの名前。 この値は 1024 文字を超えない必要があります。  
  
 `pMetaData`  
 [in]参照アセンブリのバージョン、プラットフォーム、ロケール情報を含む ASSEMBLYMETADATA インスタンス。  
  
 `pbHashValue`  
 [in]参照先のアセンブリに関連付けられたデータをハッシュします。 任意。  
  
 `cbHashValue`  
 [in]バイト サイズ`pbHashValue`します。  
  
 `dwAssemblyRefFlags`  
 [in]ビットごとの組み合わせ[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)実行エンジンの動作を制御する値。  
  
 `pmdar`  
 [out]返されたポインター`AssemblyRef`メタデータ トークン。  
  
## <a name="remarks"></a>Remarks  
 1 つ`AssemblyRef`このアセンブリを参照する各アセンブリのメタデータ構造を定義する必要があります。  
  
 実行時に、参照先アセンブリの詳細については、"ビルド"と情報を表すことを示す値をアセンブリの競合回避モジュールに渡されます。 アセンブリ リゾルバーは、ポリシーを適用します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
