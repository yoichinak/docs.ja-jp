---
title: IHostPolicyManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: db089a55128fa675ceedf157b046fe205d8c6b51
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804338"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager インターフェイス
中止、タイムアウト、またはエラーが発生した場合に共通言語ランタイム (CLR) が実行するアクションをホストに通知するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[OnDefaultAction メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|CLR が、スレッドの中止またはアンロードに応答して[ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md)の呼び出しによって指定された既定のアクションを実行しようとしていることをホストに通知し <xref:System.AppDomain> ます。|  
|[OnFailure メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|リソース割り当てまたは再利用エラーに応答して、CLR が[ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)の呼び出しによって指定されたアクションを実行しようとしていることをホストに通知します。|  
|[OnTimeout メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|タイムアウトに応答して[ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md)への呼び出しによって指定されたアクションを CLR が実行しようとしていることをホストに通知します。|  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [EClrFailure 列挙型](eclrfailure-enumeration.md)
- [EClrOperation 列挙型](eclroperation-enumeration.md)
- [EPolicyAction 列挙型](epolicyaction-enumeration.md)
- [ICLRPolicyManager インターフェイス](iclrpolicymanager-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
