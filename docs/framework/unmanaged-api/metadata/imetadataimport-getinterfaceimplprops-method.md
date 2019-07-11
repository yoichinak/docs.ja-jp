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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a4305b94d785a764671a2d73f43facefd0da0e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782369"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps メソッド
メタデータ トークンへのポインターを取得、<xref:System.Type>指定されたメソッドを実装して、そのメソッドを宣言するインターフェイス。
  
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
 [in]クラスとインターフェイスのトークンを返すメソッドを表すメタデータ トークンです。  
  
 `pClass`  
 [out]メソッドを実装するクラスを表すメタデータ トークンです。  
  
 `ptkIface`  
 [out]実装されたメソッドを定義するインターフェイスを表すメタデータ トークンです。  

## <a name="remarks"></a>Remarks

 値を取得する`iImpl`呼び出すことによって、 [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md)メソッド。
 
 たとえば、クラスがあること、 `mdTypeDef` 0x02000007 という値と型を持つトークンがある 3 つのインターフェイスを実装するトークンします。 

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

概念的には、この情報は、インターフェイスの実装としてテーブルに格納されます。

| 行番号 | クラスのトークン | トークンをインターフェイスします。 |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

トークンが 4 バイトの値を思い出してください。

- 下位 3 バイトは、行番号を保持または削除します。
- 上位バイトを保持するトークンの種類 – の 0x09`mdtInterfaceImpl`します。

`GetInterfaceImplProps` 行で指定したトークンに保持されている情報を返します、`iImpl`引数。 
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
