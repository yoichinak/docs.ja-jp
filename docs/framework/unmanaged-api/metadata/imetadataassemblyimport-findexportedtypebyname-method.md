---
title: IMetaDataAssemblyImport::FindExportedTypeByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7575659441b2eae37365c10050bca53e0cfdef6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473917"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a>IMetaDataAssemblyImport::FindExportedTypeByName メソッド
名前およびそれを囲む型を指定するエクスポートされた型、ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szName`  
 [in]エクスポートされる型の名前。  
  
 `mdtExportedType`  
 [in]エクスポートされた型の外側のクラスのメタデータ トークン。 この値は`mdExportedTypeNil`型が入れ子になった型ではない場合は、要求されたエクスポートします。  
  
 `ptkExportedType`  
 [out]ポインター、`mdExportedType`エクスポートされる型を表すトークン。  
  
## <a name="remarks"></a>Remarks  
 `FindExportedTypeByName`メソッドは、参照を解決するための共通言語ランタイムによって使用されている標準の規則を使用します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [ランタイムがアセンブリを検索する方法](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
