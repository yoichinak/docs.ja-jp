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
ms.openlocfilehash: f881440b2e93745723bd090cfbab0286dcd0a4e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937869"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore インターフェイス
共通言語ランタイム (CLR) とは独立して、ホストがアセンブリとモジュールを読み込むことができるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ProvideAssembly メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|[IHostAssemblyManager:: GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)の呼び出しから返された[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)によって参照されていないアセンブリへの参照を取得します。|  
|[ProvideModule メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|アセンブリ内のモジュール、またはリンクされた (埋め込まれていない) リソースファイル内のモジュールを解決します。|  
  
## <a name="remarks"></a>Remarks  
 `IHostAssemblyStore`ホストがアセンブリ id に基づいてアセンブリを効率的に読み込む方法を提供します。 ホストは、バイトを直接`IStream`指し示すインスタンスを返すことによって、アセンブリを読み込みます。  
  
 CLR は、初期化時にを呼び`IHostAssemblyStore`出す`IHostAssemblyManager::GetNonHostAssemblyStores`ことによってホストが実装されているかどうかを判断します。 これにより、ホストは、たとえば、ユーザーアセンブリへのバインドを制御できますが、ランタイムに依存して .NET Framework アセンブリにバインドすることができます。  
  
> [!NOTE]
> の`IHostAssemblyStore`実装を提供する場合、ホストはから`ICLRAssemblyReferenceList` `IHostAssemblyManager::GetNonHostStoreAssemblies`返されたによって参照されていないすべてのアセンブリを解決するための目的を指定します。  
  
> [!NOTE]
> .NET Framework バージョン2.0 では、[ネイティブイメージジェネレーター (ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)ユーティリティによって提供されるアセンブリのネイティブイメージをホストが読み込む方法は提供されていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
