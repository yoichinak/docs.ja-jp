---
title: EMemoryCriticalLevel 列挙型
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ee8705d00e1f63f69863d0bf8e7d0d9d62807e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122292"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel 列挙型
特定のメモリ割り当てが要求されましたが満足することはできません、障害の影響を示す値が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eAppDomainCritical`|割り当てが、割り当てが要求したドメイン内のマネージ コードを実行するための重要なことを示します。 メモリの割り当てができない場合、CLR がドメインに引き続き使用できることを保証することはできません。 ホストは、割り当てを満たすことができない場合に実行するアクションを決定します。 中止する CLR に指示することができますが、`AppDomain`自動的にメソッドを呼び出すことによって実行を継続することを許可または[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。|  
|`eProcessCritical`|割り当てが、プロセス内のマネージ コードの実行に不可欠であることを示します。 この値は、ファイナライザーを実行するときに起動中に、を使用されます。 メモリの割り当てができない場合、プロセスで、CLR は動作できません。 割り当てに失敗した場合、CLR は無効になります。 CLR にすべての後続の呼び出しは、HOST_E_CLRNOTAVAILABLE で失敗します。|  
|`eTaskCritical`|割り当てが、割り当てが要求したタスクを実行する重要なことを示します。 メモリの割り当てができない場合、CLR は、タスクを実行できることを保証できません。 CLR を発生させる障害が発生した場合、<xref:System.Threading.ThreadAbortException>物理操作システムのスレッドで。|  
  
## <a name="remarks"></a>Remarks  
 定義されているメモリの割り当て方法、 [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)と[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)インターフェイスは、この型のパラメーターを受け取る。 エラーの重大度に応じて、ホストを決定できます、割り当て要求をすぐに失敗するか、満たすことができるまで待機するかどうか。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRMemoryNotificationCallback インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [ホスティングの列挙体](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
