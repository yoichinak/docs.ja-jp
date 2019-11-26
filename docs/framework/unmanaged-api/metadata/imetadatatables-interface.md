---
title: IMetaDataTables インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: 17305f2c088dd6f479da4c823d3db0fd50c0b3d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443227"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables インターフェイス
テーブル内のメタデータ情報の格納と取得のためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBlob メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Gets a pointer to the binary large object (BLOB) at the specified column index.|  
|[GetBlobHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|Gets the size, in bytes, of the BLOB heap.|  
|[GetCodedTokenInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Gets a pointer to an array of tokens associated with the specified row index.|  
|[GetColumn メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.|  
|[GetColumnInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Gets data about the specified column in the specified table.|  
|[GetGuid メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Gets a GUID from the row at the specified index.|  
|[GetGuidHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|Gets the size, in bytes, of the GUID heap.|  
|[GetNextBlob メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Gets the index of the next BLOB in the table.|  
|[GetNextGuid メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Gets the index of the next GUID value in the current table column.|  
|[GetNextString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Gets the index of the next string in the current table column.|  
|[GetNextUserString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Gets the index of the row that contains the next hard-coded string in the current table column.|  
|[GetNumTables メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Gets the number of tables in the scope of the current `IMetaDataTables` instance.|  
|[GetRow メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Gets the row at the specified row index, in the table at the specified table index.|  
|[GetString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Gets the string at the specified index from the table column in the current reference scope.|  
|[GetStringHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Gets the size, in bytes, of the string heap.|  
|[GetTableIndex メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Gets the index for the table referenced by the specified token.|  
|[GetTableInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.|  
|[GetUserString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Gets the hard-coded string at the specified index in the string column in the current scope.|  
|[GetUserStringHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Gets the size, in bytes, of the user string heap.|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
