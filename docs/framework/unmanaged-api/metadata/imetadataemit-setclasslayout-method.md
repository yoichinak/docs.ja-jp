---
title: IMetaDataEmit::SetClassLayout メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80bf9de3eb274bf536b2794ba2ed14e7e9b553cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050052"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout メソッド
前回の呼び出しで定義されているクラスのフィールドのレイアウトが完了すると[DefineTypeDef メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]`mdTypeDef`クラスに配置されることを示すトークン。  
  
 `dwPackSize`  
 [in]パッキング サイズ:1、2、4、8 または 16 バイト数。 パッキング サイズには、横にあるフィールド間のバイト数です。  
  
 `rFieldOffsets`  
 [in]配列の[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)構造体、クラスのフィールドとフィールドのオフセットされている場合、クラス内でそれぞれを指定します。 終了、配列の`mdTokenNil`します。  
  
 `ulClassSize`  
 [in]クラスのバイト単位のサイズ。  
  
## <a name="remarks"></a>Remarks  
 クラスが最初に呼び出すことによって定義されている、 [imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)メソッド、およびクラスのフィールドの 3 つのレイアウトのいずれかを指定する: 自動、順次、または明示的な。 通常、自動レイアウトを使用し、ランタイムでフィールドをレイアウトする最善の方法を選択できるようにします。  
  
 ただし、フィールドをアンマネージ コードが使用する配置に従ってレイアウトたい場合があります。 この場合、レイアウトがシーケンシャルまたは明示的のいずれかと呼び出しを選択`SetClassLayout`フィールドのレイアウトを完了します。  
  
- シーケンシャル レイアウト:パッキング サイズを指定します。 本来のサイズまたはパッキング サイズより小さなオフセット フィールドのいずれかの結果のいずれかに従って、フィールドが配置されます。 設定`rFieldOffsets`と`ulClassSize`をゼロにします。  
  
- 明示的なレイアウト:各フィールドのオフセットを指定するか、クラスのサイズとパッキング サイズを指定します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
