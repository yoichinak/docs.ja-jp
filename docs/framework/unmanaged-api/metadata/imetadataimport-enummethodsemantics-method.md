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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6021cd0126f4dd85b796a3110cd95a83c0f77ff4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466792"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics メソッド
指定したメソッドが関連付けられているプロパティおよびプロパティ変更イベントを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [入力、出力]列挙子へのポインター。 このメソッドの最初の呼び出しで NULL があります。  
  
 `mb`  
 [in]列挙体のスコープを制限する MethodDef トークンです。  
  
 `rEventProp`  
 [out]イベントまたはプロパティを格納する配列。  
  
 `cMax`  
 [in] `rEventProp` 配列の最大サイズ。  
  
 `pcEventProp`  
 [out]イベントまたはプロパティで返される数`rEventProp`します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` 正常に返されます。|  
|`S_FALSE`|イベントまたはプロパティを列挙するためにはありません。 その場合は、`pcEventProp`は 0 です。|  
  
## <a name="remarks"></a>Remarks  
 多くの共通言語ランタイム型を定義*プロパティ*`Changed`イベントと`On`*プロパティ*`Changed`それらのプロパティに関連するメソッド。 たとえば、<xref:System.Windows.Forms.Control?displayProperty=nameWithType>型を定義しますを<xref:System.Windows.Forms.Control.Font%2A>プロパティ、<xref:System.Windows.Forms.Control.FontChanged>イベント、および<xref:System.Windows.Forms.Control.OnFontChanged%2A>メソッド。 Set アクセサー メソッド、<xref:System.Windows.Forms.Control.Font%2A>プロパティ呼び出し<xref:System.Windows.Forms.Control.OnFontChanged%2A>メソッドを生成させる、<xref:System.Windows.Forms.Control.FontChanged>イベント。 呼び出しは`EnumMethodSemantics`の MethodDef を使用して<xref:System.Windows.Forms.Control.OnFontChanged%2A>への参照を取得する、<xref:System.Windows.Forms.Control.Font%2A>プロパティおよび<xref:System.Windows.Forms.Control.FontChanged>イベント。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
