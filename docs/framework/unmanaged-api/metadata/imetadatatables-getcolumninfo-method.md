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
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177118"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo メソッド
指定したテーブルの指定した列に関するデータを取得します。  
  
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
 [in]目的のテーブルのインデックス。  
  
 `ixCol`  
 [in]目的の列のインデックス。  
  
 `poCol`  
 [アウト]行の列のオフセットへのポインター。  
  
 `pcbCol`  
 [アウト]列のサイズ (バイト単位) へのポインター。  
  
 `pType`  
 [アウト]列の値の型へのポインター。  
  
 `ppName`  
 [アウト]列名へのポインターへのポインター。  

## <a name="remarks"></a>解説

返される列の型は、値の範囲内にあります。

| pタイプ                    | 説明   | ヘルパー関数                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)   | 解消           | **イスリッドタイプ**<br>**イスリドールトークン** |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | コード化されたトークン | **タイプを指定します。** <br>**イスリドールトークン** |
| `iSHORT`(96)            | Int16         | **型指定**                   |
| `iUSHORT`(97)           | UInt16        | **型指定**                   |
| `iLONG`(98)             | Int32         | **型指定**                   |
| `iULONG`(99)            | UInt32        | **型指定**                   |
| `iBYTE`(100)            | Byte          | **型指定**                   |
| `iSTRING`(101)          | String        | **型指定**                    |
| `iGUID`(102)            | Guid          | **型指定**                    |
| `iBLOB`(103)            | BLOB          | **型指定**                    |

*ヒープ*に格納されている値 ( つまり、 `IsHeapType == true`) は、次の方法で読み取ることができます。

- `iSTRING`:**取得文字列**
- `iGUID`を取得**します。**
- `iBLOB`を取得**します。**

> [!IMPORTANT]
> 上記の表で定義されている定数を使用するには`#define _DEFINE_META_DATA_META_CONSTANTS`*、cor.h*ヘッダー ファイルによって提供されるディレクティブをインクルードします。

## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataTables インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
