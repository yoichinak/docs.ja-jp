---
title: IMetaDataImport::EnumMethodSemantics メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175461"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics メソッド
指定したメソッドが関連付けられているプロパティおよびプロパティ変更イベントを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [イン、アウト]列挙子へのポインター。 このメソッドの最初の呼び出しでは、NULL にする必要があります。  
  
 `mb`  
 [in]列挙のスコープを制限する MethodDef トークン。  
  
 `rEventProp`  
 [アウト]イベントまたはプロパティを格納するために使用される配列。  
  
 `cMax`  
 [in] `rEventProp` 配列の最大サイズ。  
  
 `pcEventProp`  
 [アウト]で返されるイベントまたはプロパティの`rEventProp`数。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`正常に返されました。|  
|`S_FALSE`|列挙するイベントまたはプロパティはありません。 その場合は、`pcEventProp`ゼロです。|  
  
## <a name="remarks"></a>解説  
 多くの共通言語ランタイム型は *、プロパティ*`Changed``On`イベントとプロパティに関連する*プロパティ*`Changed`メソッドを定義します。 たとえば、型は<xref:System.Windows.Forms.Control?displayProperty=nameWithType><xref:System.Windows.Forms.Control.Font%2A>プロパティ、イベント、およびメソッド<xref:System.Windows.Forms.Control.FontChanged>を定義します<xref:System.Windows.Forms.Control.OnFontChanged%2A>。 プロパティの set アクセサ<xref:System.Windows.Forms.Control.Font%2A>メソッド<xref:System.Windows.Forms.Control.OnFontChanged%2A>はメソッドを呼び出し、<xref:System.Windows.Forms.Control.FontChanged>イベントを発生させます。 プロパティとイベント`EnumMethodSemantics`への参照を取得するには<xref:System.Windows.Forms.Control.OnFontChanged%2A>、 メソッド定義を<xref:System.Windows.Forms.Control.Font%2A>使用して呼<xref:System.Windows.Forms.Control.FontChanged>び出します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
