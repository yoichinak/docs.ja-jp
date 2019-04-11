---
title: IMetaDataDispenserEx インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96475086b1244ae75ed692dd10cb693af0be9af7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186954"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx インターフェイス
拡張、 [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)の現在のメタデータ スコープにメタデータ Api の動作を制御する機能を提供するインターフェイス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[FindAssembly メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|このメソッドは実装されていません。 呼び出された場合、E_NOTIMPL を返します。|  
|[FindAssemblyModule メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|このメソッドは実装されていません。 呼び出された場合、E_NOTIMPL を返します。|  
|[GetCORSystemDirectory メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|現在の共通言語ランタイム (CLR) を保持するディレクトリを取得します。 このメソッドは、プロセス外のデバッガーでのみサポートします。 別のコンポーネントから呼び出す場合、E_NOTIMPL を返します。|  
|[GetOption メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|現在のメタデータ スコープの指定したオプションの値を取得します。 オプションは、現在のメタデータ スコープへの呼び出しを処理する方法を制御します。|  
|[OpenScopeOnITypeInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|このメソッドは実装されていません。 呼び出された場合、E_NOTIMPL を返します。|  
|[SetOption メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|現在のメタデータ スコープの指定した値に指定されたオプションを設定します。 オプションは、現在のメタデータ スコープへの呼び出しを処理する方法を制御します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
