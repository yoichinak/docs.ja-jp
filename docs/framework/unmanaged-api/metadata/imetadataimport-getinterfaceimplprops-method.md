---
title: IMetaDataImport::GetInterfaceImplProps メソッド
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175383"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps メソッド
指定したメソッドを実装するメタデータ<xref:System.Type>トークン、およびそのメソッドを宣言するインターフェイスのメタデータ トークンへのポインターを取得します。
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `iiImpl`  
 [in]クラス トークンとインターフェイス トークンを返すメソッドを表すメタデータ トークン。  
  
 `pClass`  
 [アウト]メソッドを実装するクラスを表すメタデータ トークン。  
  
 `ptkIface`  
 [アウト]実装されたメソッドを定義するインターフェイスを表すメタデータ トークン。  

## <a name="remarks"></a>解説

 メソッドを呼び出`iImpl`すことによって値[を取得します](imetadataimport-enuminterfaceimpls-method.md)。

 たとえば、クラスの`mdTypeDef`トークン値が 0x0200007 で、型にトークンを持つ 3 つのインターフェイスを実装しているとします。

- 0x02000003 (タイプ定義)
- 0x010000A (タイプレファレンス)
- 0x0200001C (タイプ定義)

概念的には、この情報は次のようにインターフェイス実装テーブルに格納されます。

| 行番号 | クラストークン | インターフェイス トークン |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

このトークンは 4 バイトの値です。

- 下位 3 バイトは行番号(RID)を保持します。
- 上位バイトはトークンタイプを保持します – 0x09 for `mdtInterfaceImpl`.

`GetInterfaceImplProps`は、引数に指定したトークンの行に保持されている情報`iImpl`を返します。
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
