---
title: IMetaDataTables::GetColumnInfo メソッド
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd67d9faafedf4fb92c69618d4464ebb2ce47dcc
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774260"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo メソッド
指定されたテーブル内の指定された列に関するデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a>パラメーター
=======

 `ixTbl`  
 から目的のテーブルのインデックス。  
  
 `ixCol`  
 から目的の列のインデックス。  
  
 `poCol`  
 入出力行内の列のオフセットへのポインター。  
  
 `pcbCol`  
 入出力列のサイズ (バイト単位) へのポインター。  
  
 `pType`  
 入出力列内の値の型へのポインター。  
  
 `ppName`  
 入出力列名へのポインターへのポインター。  
 
## <a name="remarks"></a>Remarks

返される列の型は、値の範囲内にあります。

| pType                    | 説明   | ヘルパー関数                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)   | Rid           | **IsRidType**<br>**IsRidOrToken** |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | コード化されたトークン | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT` (96)            | Int16         | **IsFixedType**                   |
| `iUSHORT` (97)           | UInt16        | **IsFixedType**                   |
| `iLONG` (98)             | Int32         | **IsFixedType**                   |
| `iULONG` (99)            | UInt32        | **IsFixedType**                   |
| `iBYTE` (100)            | Byte          | **IsFixedType**                   |
| `iSTRING` (101)          | 文字列型        | **IsHeapType**                    |
| `iGUID` (102)            | GUID          | **IsHeapType**                    |
| `iBLOB` (103)            | Blob          | **IsHeapType**                    |

*ヒープ*に格納されている値 (つまり `IsHeapType == true`) は、次の方法で読み取ることができます。

- `iSTRING`: **Imetadatatables**
- `iGUID`: **Imetadatatables 実行できます。 GetGUID**
- `iBLOB`: **Imetadatatables 実行できます。 GetBlob**

> [!IMPORTANT]
> 上の表で定義されている定数を使用するには、 *cor*ヘッダーファイルによって提供されるディレクティブ `#define _DEFINE_META_DATA_META_CONSTANTS` を含めます。

## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** Mscoree.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataTables インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
