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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b2298e2d67e8a50e11d53d864f0e78f3b549e45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131418"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables インターフェイス
テーブル内のメタデータ情報の格納と取得のためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBlob メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|指定した列のインデックス位置にあるバイナリ ラージ オブジェクト (BLOB) へのポインターを取得します。|  
|[GetBlobHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|BLOB ヒープのバイト単位のサイズを取得します。|  
|[GetCodedTokenInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|指定した行のインデックスに関連付けられているトークンの配列へのポインターを取得します。|  
|[GetColumn メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|指定したテーブルのインデックス位置にあるテーブル内で指定された列のインデックス位置にある列に含まれる値にポインターを取得します。|  
|[GetColumnInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|指定されたテーブルで指定された列に関するデータを取得します。|  
|[GetGuid メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|指定したインデックス位置の行から GUID を取得します。|  
|[GetGuidHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|GUID ヒープのバイト単位のサイズを取得します。|  
|[GetNextBlob メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|テーブル内には、次の BLOB のインデックスを取得します。|  
|[GetNextGuid メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|現在のテーブルの列には、次の GUID 値のインデックスを取得します。|  
|[GetNextString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|現在のテーブルの列には、次の文字列のインデックスを取得します。|  
|[GetNextUserString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|現在のテーブル列で [次へ]、ハード コーディングされた文字列を含む行のインデックスを取得します。|  
|[GetNumTables メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|現在のスコープ内のテーブルの数を取得`IMetaDataTables`インスタンス。|  
|[GetRow メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|指定したテーブルのインデックス位置にある表に、指定した行インデックス位置にある行を取得します。|  
|[GetString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|参照の現在のスコープ内のテーブル列から、指定したインデックス位置にある文字列を取得します。|  
|[GetStringHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|文字列ヒープのバイト単位のサイズを取得します。|  
|[GetTableIndex メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|指定したトークンによって参照されるテーブルのインデックスを取得します。|  
|[GetTableInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|指定したテーブルのインデックス位置にある、名、行のサイズ、行の数、列の数と、テーブルのキー列のインデックスを取得します。|  
|[GetUserString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|現在のスコープ内で文字列の列で指定したインデックス位置には、ハード コーディングされた文字列を取得します。|  
|[GetUserStringHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|ユーザー文字列ヒープのバイト単位のサイズを取得します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
