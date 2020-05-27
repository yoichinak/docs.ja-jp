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
ms.openlocfilehash: 22c0a317777a12294ba7a90f7af1ceeca3ad0a47
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009263"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize メソッド
現在のスコープ内のアセンブリとそのメタデータの推定バイナリサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `fSave`  
 から正確またはおおよそのサイズを取得するかどうかを指定する[CorSaveSize](corsavesize-enumeration.md)列挙体の値。 有効な値は、cssAccurate、cssQuick、cssDiscardTransientCAs の3つだけです。  
  
- cssAccurate は正確な保存サイズを返しますが、計算にかかる時間は長くなります。  
  
- cssQuick は、サイズを返します。これは安全性のために埋め込まれていますが、計算にかかる時間は短くなります。  
  
- cssDiscardTransientCAs `GetSaveSize` は、破棄可能なカスタム属性を破棄できることを示します。  
  
 `pdwSaveSize`  
 入出力ファイルを保存するために必要なサイズへのポインター。  
  
## <a name="remarks"></a>コメント  
 `GetSaveSize`現在のスコープ内のアセンブリとそのすべてのメタデータを保存するために必要な領域をバイト単位で計算します。 ( [IMetaDataEmit:: SaveToStream](imetadataemit-savetostream-method.md)メソッドを呼び出すと、このバイト数が出力されます)。  
  
 呼び出し元が[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)インターフェイス ( [IMetaDataEmit:: SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)または[IMetaDataEmit:: Merge](imetadataemit-merge-method.md)) を実装している場合、 `GetSaveSize` はメタデータに対して2つのパスを実行し、最適化および圧縮します。 それ以外の場合、最適化は実行されません。  
  
 最適化が実行された場合、最初のパスは単にメタデータ構造を並べ替えて、インポート時の検索のパフォーマンスを調整します。 この手順では、通常、後で参照するためにツールによって保持されているトークンが無効になるという副作用で、レコードを移動します。 ただし、メタデータは、2番目のパスの後に、これらのトークンの変更を呼び出し元に通知しません。 2番目のパスでは、 `mdTypeRef` `mdMemberRef` 現在のメタデータスコープ内で宣言されている型またはメンバーへの参照である場合に、メタデータの全体的なサイズを減らす (事前バインディング)、トークンなどのさまざまな最適化が実行されます。 このパスでは、別のトークンマッピングのラウンドが発生します。 このパスが経過すると、メタデータエンジンは、 `IMapToken` 変更されたトークン値のインターフェイスを介して呼び出し元に通知します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** Mscoree.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
