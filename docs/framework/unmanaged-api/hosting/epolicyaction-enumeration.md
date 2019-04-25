---
title: EPolicyAction 列挙型
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75bd7da67cbac958f0b34c8295454a719962c7ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201729"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction 列挙型
ホストを設定できますで説明されている操作のポリシーのアクションについて説明します[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)しで説明されているエラー [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eAbortThread`|共通言語ランタイム (CLR) の中止でスレッドが適切に処理する必要がありますを指定します。 適切な中止には、すべてを実行する試行が含まれています。`finally`いずれかのブロック`catch`スレッドの中止、およびファイナライザーに関連するブロック。|  
|`eDisableRuntime`|CLR が無効の状態を入力する必要がありますを指定します。 マネージ コードを実行して、影響を受けるプロセスでそれ以上と、CLR に入るをスレッドがブロックされます。|  
|`eExitProcess`|CLR がファイナライザーを実行して、クリーンアップとログ記録操作を実行するなど、プロセスの正常な終了を試みる必要があることを指定します。|  
|`eFastExitProcess`|CLR しないで終了すること、プロセス、すぐにファイナライザーを実行するか、クリーンアップとログ記録操作を実行するを指定します。 ただし、デバッガーに通知が送信されます。|  
|`eNoAction`|アクションを実行しないことを指定します。|  
|`eRudeAbortThread`|CLR がルード スレッドの中止を実行する必要がありますを指定します。 だけ`catch`と`finally`でマークされたブロック<xref:System.EnterpriseServices.MustRunInClientContextAttribute>実行されます。|  
|`eRudeExitProcess`|CLR がファイナライザーを実行するか、操作のログ記録しないでプロセスを終了することを指定します。|  
|`eRudeUnloadAppDomain`|CLR がのルード アンロードを実行する必要がありますを指定します、<xref:System.AppDomain>します。 マークされた唯一のファイナライザー<xref:System.EnterpriseServices.MustRunInClientContextAttribute>実行されます。 これと同様に、すべてのスレッド<xref:System.AppDomain>スタックには、受信、 `ThreadAbortException`、だけが`catch`と`finally`でマークされたブロック<xref:System.EnterpriseServices.MustRunInClientContextAttribute>実行されます。|  
|`eThrowException`|メモリ不足、バッファーのオーバーフローなどの条件に該当する例外をスローすることを指定します。|  
|`eUnloadAppDomain`|指定します、<xref:System.AppDomain>がアンロードされます。 CLR は、ファイナライザーを実行しようとします。|  
  
## <a name="remarks"></a>Remarks  
 ホストのメソッドを呼び出すことによってポリシーのアクションを設定する、 [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)インターフェイス。 ルードと正常な中止の詳細については、次を参照してください。、 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)列挙体。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [EClrFailure 列挙型](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [ICLRPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
