---
title: IMetaDataImport::GetEventProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177266"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps メソッド
宣言型、デリゲートの add メソッドと remove メソッド、フラグおよびその他の関連付けられたデータなど、指定したイベント トークンによって表されるイベントのメタデータ情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,
   [out] LPCWSTR       szEvent,
   [in]  ULONG         cchEvent,
   [out] ULONG         *pchEvent,
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,
   [out] mdMethodDef   *pmdRemoveOn,
   [out] mdMethodDef   *pmdFire,
   [out] mdMethodDef   rmdOtherMethod[],
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ev`  
 [in]メタデータを取得するイベントを表すイベント メタデータ トークン。  
  
 `pClass`  
 [アウト]イベントを宣言するクラスを表す TypeDef トークンへのポインター。  
  
 `szEvent`  
 [アウト]によって`ev`参照されるイベントの名前。  
  
 `pchEvent`  
 [in]要求された長さは、 の`szEvent`ワイド文字で表示されます。  
  
 `pdwEventFlags`  
 [アウト]返される長さは、 の`szEvent`ワイド文字で返されます。  
  
 `ptkEventType`  
 [アウト]イベントの型を表す<xref:System.Delegate>TypeRef または TypeDef メタデータ トークンへのポインター。  
  
 `pmdAddOn`  
 [アウト]イベントのハンドラーを追加するメソッドを表すメタデータ トークンへのポインター。  
  
 `pmdRemoveOn`  
 [アウト]イベントのハンドラーを削除するメソッドを表すメタデータ トークンへのポインター。  
  
 `pmdFire`  
 [アウト]イベントを発生させるメソッドを表すメタデータ トークンへのポインター。  
  
 `rmdOtherMethod`  
 [アウト]イベントに関連付けられた他のメソッドへのトークン ポインターの配列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 配列の最大サイズ。  
  
 `pcOtherMethod`  
 [アウト]に返される`rmdOtherMethod`トークンの数。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
