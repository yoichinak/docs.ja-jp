---
title: IHostAssemblyManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: 8106dd70f6c4099b2246530622f0845f22a0c53f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805052"
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager インターフェイス
共通言語ランタイム (CLR) またはホストによって読み込まれる必要があるアセンブリのセットをホストが指定できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetAssemblyStore メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|ホストによって読み込まれたアセンブリの一覧を表す[IHostAssemblyStore](ihostassemblystore-interface.md)へのインターフェイスポインターを取得します。|  
|[GetNonHostStoreAssemblies メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|ホストが CLR を読み込むことを想定しているアセンブリの一覧を表す[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)へのインターフェイスポインターを取得します。|  
  
## <a name="remarks"></a>解説  
 ホストがまたはを実装する必要はありません `IHostAssemblyManager` `IHostAssemblyStore` 。 ホストがを実装している場合は `IHostAssemblyManager` 、も実装する必要があり `IHostAssemblyStore` ます。  
  
 ランタイムは、 `IHostAssemblyManager` 初期化時に IID_IHostAssemblyManager のを使用して[IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md)を呼び出すことにより、を照会し `IID` ます。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyReferenceList インターフェイス](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyStore インターフェイス](ihostassemblystore-interface.md)
- [IHostControl インターフェイス](ihostcontrol-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
