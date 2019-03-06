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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f2eec9fce1909f6a83190f5ba3e99162461bbc4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492154"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps メソッド
宣言する型の追加と削除メソッドのデリゲート、任意のフラグと関連付けられているその他のデータを含め、指定したイベント トークンによって表されるイベントのメタデータ情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]メタデータを取得するイベントを表すイベントのメタデータ トークンです。  
  
 `pClass`  
 [out]イベントを宣言するクラスを表す TypeDef トークンへのポインター。  
  
 `szEvent`  
 [out]によって参照されるイベントの名前`ev`します。  
  
 `pchEvent`  
 [in]要求された長さのワイド文字で`szEvent`します。  
  
 `pdwEventFlags`  
 [out]ワイド文字で返される長さ`szEvent`します。  
  
 `ptkEventType`  
 [out]TypeRef または TypeDef メタデータ トークンを表すへのポインター、<xref:System.Delegate>イベントの種類。  
  
 `pmdAddOn`  
 [out]イベントのハンドラーを追加するメソッドを表すメタデータ トークンへのポインター。  
  
 `pmdRemoveOn`  
 [out]イベントのハンドラーを削除するメソッドを表すメタデータ トークンへのポインター。  
  
 `pmdFire`  
 [out]イベントを発生させるメソッドを表すメタデータ トークンへのポインター。  
  
 `rmdOtherMethod`  
 [out]イベントに関連付けられているその他のメソッドへのトークンのポインターの配列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 配列の最大サイズ。  
  
 `pcOtherMethod`  
 [out]トークンで返される数`rmdOtherMethod`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
