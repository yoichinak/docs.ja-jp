---
title: ICLRMetaHostPolicy インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2735d3e0bbcb6326ca8ea87a3358824bca81108
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951188"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy インターフェイス
[Getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)メソッドを提供します。このメソッドは、ポリシー条件、マネージアセンブリ、バージョン、および構成ファイルに基づいて共通言語ランタイム (CLR) インターフェイスへのポインターを返します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetRequestedRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|ポリシー条件、マネージアセンブリ、バージョン、および構成ファイルに基づいて、優先する CLR インターフェイスを提供します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスへの参照を取得するには、次のコードに示すように[Clrcreateinstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)関数を呼び出します。  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> このインターフェイスは、実際には CLR の読み込みもアクティブ化も行いませんが、インストールまたは読み込まれている使用可能なバージョンに基づいて、単純に優先 CLR バージョンを返します。  
  
 .NET Framework 4 ホスト API はポリシーを統合して、特定のニーズを持つホストが、意図しない罰則を伴わずに基本的な機能を使用できるようにします。 たとえば、多くの Mscoree.dll のエクスポートは特定の CLR にバインドされますが、メソッドでは論理的に要求されない場合もあります。 [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)列挙体は、ほとんどのホストに共通のバインドポリシーを提供します。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
