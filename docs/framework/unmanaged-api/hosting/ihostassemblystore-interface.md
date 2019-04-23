---
title: IHostAssemblyStore インターフェイス
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4067c1fbcf99c903c892eaec58262d95569114b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173421"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore インターフェイス
アセンブリおよび共通言語ランタイム (CLR) とは無関係にモジュールの読み込みにホストできるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ProvideAssembly メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|によって参照されているアセンブリへの参照を取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)への呼び出しから返された[ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)します。|  
|[ProvideModule メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|アセンブリまたはリンク (組み込まれていない) リソース ファイル内のモジュールを解決します。|  
  
## <a name="remarks"></a>Remarks  
 `IHostAssemblyStore` ホストがアセンブリ id に基づいた効率的にアセンブリを読み込む方法を提供します。 ホストでは、アセンブリを読み込んで返すことによって`IStream`バイトを直接ポイントするインスタンス。  
  
 CLR は、ホストが実装されているかどうかを決定します。`IHostAssemblyStore`呼び出して`IHostAssemblyManager::GetNonHostAssemblyStores`の初期化時にします。 これにより、ホスト、たとえば、.NET Framework アセンブリへのバインドをランタイムに依存するが、ユーザーのアセンブリへのバインディングを制御します。  
  
> [!NOTE]
>  実装を提供するために`IHostAssemblyStore`、ホストによって参照されていないすべてのアセンブリを解決するのにはその目的を指定します、`ICLRAssemblyReferenceList`から返された`IHostAssemblyManager::GetNonHostStoreAssemblies`します。  
  
> [!NOTE]
>  によって提供される、.NET Framework version 2.0 が、ホスト、アセンブリのネイティブ イメージを読み込むための手段を提供しない、[ネイティブ イメージ ジェネレーター (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)ユーティリティ。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
