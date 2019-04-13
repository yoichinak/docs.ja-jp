---
title: IMetaDataImport::EnumUnresolvedMethods メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e6e53f69f58c2f5778083d9b8f8be466b952cdd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090252"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a>IMetaDataImport::EnumUnresolvedMethods メソッド
現在のメタデータ スコープ内の未解決のメソッドを表す MemberDef トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [入力、出力]列挙子へのポインター。 このメソッドの最初の呼び出しで NULL があります。  
  
 `rMethods`  
 [out]MemberDef トークンを格納するために使用する配列。  
  
 `cMax`  
 [in] `rMethods` 配列の最大サイズ。  
  
 `pcTokens`  
 [out]返される MemberDef トークン数`rMethods`します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods` 正常に返されます。|  
|`S_FALSE`|トークンを列挙することはありません。 その場合は、`pcTokens`は 0 です。|  
  
## <a name="remarks"></a>Remarks  
 未解決のメソッドは宣言されましたが、実装されていません。 メソッドがマークされている場合に、列挙体のメソッドが含まれている`miForwardRef`、`mdPinvokeImpl`または`miRuntime`0 に設定されます。 つまり、未解決のメソッドは、マークされているクラス メソッド`miForwardRef`(PInvoke 経由で到達)、アンマネージ コードで実装またはランタイム自体によって内部的に実装するはありませんが、  
  
 列挙体は、モジュール スコープ (グローバル) またはインターフェイスまたは抽象クラスで定義されているすべてのメソッドを除外します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
