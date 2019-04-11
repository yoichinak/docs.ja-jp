---
title: IMetaDataEmit2 インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87b5b60d75d5d28e100ec75192d0cacf51765927
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200195"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 インターフェイス
拡張、 [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)主に、ジェネリック型を扱う機能を提供するインターフェイス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DefineGenericParam メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|ジェネリック型パラメーターの定義を作成し、そのジェネリック型パラメーターのトークンを取得します。|  
|[DefineMethodSpec メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|メソッドのジェネリック インスタンスを作成し、定義するためのトークンを取得します。|  
|[GetDeltaSaveSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|エディット コンティニュの現在のセッションの変更を表現するために必要なデータのサイズの違いを示す値を取得します。|  
|[ResetENCLog メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|エディット コンティニュは、ログをリセットし、新しいセッションを開始します。|  
|[SaveDelta メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|エディット コンティニュの現在のセッションから、指定したファイルの変更を保存します。|  
|[SaveDeltaToMemory メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|エディット コンティニュの現在のセッションからの変更をメモリに保存します。|  
|[SaveDeltaToStream メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|エディット コンティニュの現在のセッションからの変更を指定したストリームに保存します。|  
|[SetGenericParamProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|指定したトークンによって参照されているジェネリック パラメーターの定義のプロパティ値を設定します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
