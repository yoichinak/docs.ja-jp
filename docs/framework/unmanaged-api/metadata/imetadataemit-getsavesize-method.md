---
title: IMetaDataEmit::GetSaveSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d9279808e4ad15b693d06ac8a99dd33a609e5a8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992512"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize メソッド
現在のスコープ内のアセンブリとそのメタデータの推定のバイナリのサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `fSave`  
 [in]値、 [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)正確でないかおおよそのサイズを取得するかどうかを指定する列挙体。 のみの 3 つの値が無効です: cssAccurate、cssQuick、および cssDiscardTransientCAs:  
  
- cssAccurate は正確なサイズの保存を返しますが、計算に時間がかかります。  
  
- cssQuick は安全性、用に埋め込まれて、サイズを返しますが、計算時間がかかりません。  
  
- cssDiscardTransientCAs 指示`GetSaveSize`こと、破棄できる破棄できるカスタム属性。  
  
 `pdwSaveSize`  
 [out]ファイルを保存するために必要なサイズへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `GetSaveSize` 必要に応じて、(バイト単位) を現在のスコープ内でアセンブリとそのすべてのメタデータを保存する領域が計算されます。 (への呼び出し、 [imetadataemit::savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)メソッドの出力をこのバイト数)。  
  
 呼び出し元が実装されている場合、 [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)インターフェイス (を通じて[imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)または[imetadataemit::merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md))、`GetSaveSize`は 2 つのパスを実行最適化し、圧縮するメタデータ。 それ以外の場合、最適化は実行されません。  
  
 最適化を実行すると、最初のパスは単に検索のインポート時のパフォーマンスをチューニングするメタデータ構造体を並べ替えます。 この手順は、今後の参照用のツールによって保持されるトークンは無効になります影響で、レコードが移動は通常なります。 メタデータはできません、呼び出し元に通知までこれらのトークンの変更の 2 番目のパスの後ただし。 2 番目のパスのさまざまな最適化は、メタデータ、退席中 (事前バインディング) の最適化などの全体的なサイズを小さくことを意図したことがあります`mdTypeRef`と`mdMemberRef`トークンの参照が、型またはメンバーで宣言されているときに、現在のメタデータ スコープ。 このパスでは、別の一連のトークンのマッピングが発生します。 メタデータ エンジンは、このパスの後、を通じて、呼び出し元を通知しますその`IMapToken`のいずれかのインターフェイスは、トークンの値を変更します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
