---
title: IMetaDataImport::ResolveTypeRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f929e6b338d4fd48b2a6ef9588523377e0dd8faa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096063"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef メソッド
解決、<xref:System.Type>の参照を指定した TypeRef トークンによって表されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tr`  
 [in]参照先の型情報を返す TypeRef メタデータ トークンです。  
  
 `riid`  
 [in]返すインターフェイスの IID`ppIScope`します。 通常、IID_IMetaDataImport になります。  
  
 `ppIScope`  
 [out]参照先の型が定義されているモジュールのスコープへのインターフェイス。  
  
 `ptd`  
 [out]参照先の型を表す TypeDef トークンへのポインター。  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]
>  複数のアプリケーション ドメインが読み込まれている場合は、このメソッドを使用しないでください。 メソッドは、アプリケーション ドメインの境界を優先しません。 複数のバージョンのアセンブリが読み込まれると、同じ名前空間を持つ同じ型が含まれている場合は、最初に見つけた型のモジュールのスコープを返します。  
  
 `ResolveTypeRef`メソッドの他のモジュールの種類の定義を検索します。 型定義が見つかった場合`ResolveTypeRef`型の TypeDef トークンとそのモジュールのスコープのインターフェイスを返します。  
  
 型参照を解決する AssemblyRef の解決スコープがある場合、`ResolveTypeRef`メソッドのいずれかへの呼び出しで既に開かれているメタデータのスコープでのみ一致を検索、 [imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)メソッドまたは[imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)メソッド。 これは、ため`ResolveTypeRef`AssemblyRef スコープのみがディスク上またはグローバル アセンブリ キャッシュにアセンブリが格納される場所を判別することはできません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
