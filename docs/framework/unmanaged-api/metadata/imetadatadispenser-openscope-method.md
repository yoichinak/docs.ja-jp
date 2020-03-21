---
title: IMetaDataDispenser::OpenScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175942"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope メソッド
既存のディスク上のファイルを開き、そのメタデータをメモリにマップします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szScope`  
 [in]開くファイルの名前。 ファイルには、共通言語ランタイム (CLR) メタデータが含まれている必要があります。  
  
 `dwOpenFlags`  
 [in]開くときのモード (読み取り、書き込みなど) を指定する[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列挙体の値。  
  
 `riid`  
 [in]返される必要なメタデータ インターフェイスの IID。呼び出し元は、インターフェイスを使用してメタデータをインポート (読み取り) または出力 (書き込み) します。  
  
 の値は`riid`、"インポート" または "出力" インターフェイスのいずれかを指定する必要があります。 有効な値は、IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2、またはIID_IMetaDataImport2です。  
  
 `ppIUnk`  
 [アウト]返されたインターフェイスへのポインター。  
  
## <a name="remarks"></a>解説  
 メタデータのインメモリ コピーは、"import" インターフェイスの 1 つからのメソッドを使用してクエリを実行したり、"emit" インターフェイスのメソッドを使用して追加したりできます。  
  
 ターゲット ファイルに CLR メタデータが含まれていない場合`OpenScope`、メソッドは失敗します。  
  
 .NET Framework バージョン 1.0 およびバージョン 1.1 では、スコープ`dwOpenFlags`が ofRead に設定されて開かれている場合、共有の対象となります。 つまり、以前に開いたファイル`OpenScope`の名前を渡す後続の呼び出しが行われた場合、既存のスコープが再利用され、新しいデータ構造のセットは作成されません。 しかし、この共有のために問題が発生する可能性があります。  
  
 .NET Framework バージョン 2.0 では、ofRead に設定して`dwOpenFlags`開いたスコープは共有されなくなります。 の値を使用して、スコープを共有できるようにします。 スコープが共有されている場合、「読み取り/書き込み」メタデータ インターフェイスを使用するクエリは失敗します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
