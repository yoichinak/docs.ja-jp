---
title: IMetaDataTables::GetColumn メソッド
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177135"
---
# <a name="imetadatatablesgetcolumn-method"></a>IMetaDataTables::GetColumn メソッド
指定したテーブルの指定した列と行のセルに含まれる値へのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a>パラメーター

 `ixTbl`  
 [in]テーブルのインデックス。  
  
 `ixCol`  
 [in]テーブル内の列のインデックス。  
  
 `rid`  
 [in]テーブル内の行のインデックス。  
  
 `pVal`  
 [アウト]セル内の値へのポインター。  

## <a name="remarks"></a>解説

返される値の解釈は、列の`pVal`型によって異なります。 列の型は、[呼](imetadatatables-getcolumninfo-method.md)び出すことによって決定できます。

- **GetColumn**メソッドは **、Rid**型または**CodedToken**型の列を 32 ビット`mdToken`の完全な値に自動的に変換します。
- また、8 ビットまたは 16 ビットの値を 32 ビットの値に自動的に変換します。
- *ヒープ*型の列の場合、返される*pVal*は対応するヒープへのインデックスになります。

| 列の型              | pVal に含まれる | 解説                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)  | mdToken     | *pVal*には完全なトークンが含まれます。 この関数は、Rid を完全なトークンに自動的に変換します。 |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | mdToken | 戻り値が返されると *、pVal*には完全なトークンが含まれます。 この関数は、CodedToken を自動的に完全なトークンに解凍します。 |
| `iSHORT`(96)            | Int16         | 自動的に 32 ビットに拡張されます。  |
| `iUSHORT`(97)           | UInt16        | 自動的に 32 ビットに拡張されます。  |
| `iLONG`(98)             | Int32         |                                        |
| `iULONG`(99)            | UInt32        |                                        |
| `iBYTE`(100)            | Byte          | 自動的に 32 ビットに拡張されます。  |
| `iSTRING`(101)          | 文字列ヒープインデックス | *pVal*は、文字列ヒープへのインデックスです。 実際の列の文字列値を取得するには[、IMetadataTables::GetString](imetadatatables-getstring-method.md)を使用します。 |
| `iGUID`(102)            | GUID ヒープ インデックス | *pVal*は、GUID ヒープへのインデックスです。 実際の列 Guid 値を取得するには[、IMetadataTables::GetGuid](imetadatatables-getguid-method.md)を使用します。 |
| `iBLOB`(103)            | BLOB ヒープ インデックス | *pVal*は、BLOB ヒープへのインデックスです。 実際の列の BLOB 値を取得するには[、IMetadataTables::GetBlob](imetadatatables-getblob-method.md)を使用します。 |
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET フレームワークのバージョン**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataTables インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
