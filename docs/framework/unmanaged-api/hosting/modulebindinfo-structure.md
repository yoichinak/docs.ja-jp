---
title: ModuleBindInfo 構造体
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f14d3dcaad1cc8cac11599b1647d61df3a793301
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124450"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo 構造体
参照されるモジュールとそれを含んでいるアセンブリに関する詳細情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`dwAppDomainId`|一意の識別子、`IStream`への呼び出しによって返される、 [ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)参照されるモジュールの読み込み元のメソッド。|  
|`lpAssemblyIdentity`|参照されるモジュールを含むアセンブリの一意の識別子。|  
|`lpModuleName`|参照されるモジュールの名前。|  
  
## <a name="remarks"></a>Remarks  
 `ModuleBindInfo` パラメーターとして渡される`IHostAssemblyStore::ProvideModule`します。 ホスト提供の一意識別子`dwAppDomainId`共通言語ランタイム (CLR) にします。 呼び出しの後に、 [ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)ランタイム識別子を使用して判断するメソッドが返されるかどうかの内容、`IStream`マップされています。 そうである場合、ランタイムは、ストリームを再マップするのではなく、既存のコピーを読み込みます。 ランタイムは、呼び出しから返されるストリームのルックアップ キーとしてこの識別子を使用することも、`IHostAssemblyStore::ProvideAssembly`メソッド。 そのため、識別子は、アセンブリの要求とモジュールの要求も一意である必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.idl  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [AssemblyBindInfo 構造体](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
