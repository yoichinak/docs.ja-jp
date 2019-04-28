---
title: EClrOperation 列挙型
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d5f24d7415ff7ecceba6b0a5fbd3098d70dcd0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796023"
---
# <a name="eclroperation-enumeration"></a>EClrOperation 列挙型
ホストがポリシーのアクションを適用できる操作のセットについて説明します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|ホストは、ときに実行するポリシーのアクションを指定できます、<xref:System.AppDomain>非グレースフル (ルード) 方式でモジュールはアンロードされます。|  
|`OPR_AppDomainUnload`|ホストは、ときに実行するポリシーのアクションを指定できます、<xref:System.AppDomain>がアンロードされます。|  
|`OPR_FinalizerRun`|ホストは、ファイナライザーを実行するときに実行されるポリシーのアクションを指定できます。|  
|`OPR_ProcessExit`|ホストは、プロセスが終了したときに実行されるポリシーのアクションを指定できます。|  
|`OPR_ThreadAbort`|ホストは、スレッドが中止されたときに実行されるポリシーのアクションを指定できます。|  
|`OPR_ThreadRudeAbortInCriticalRegion`|ホストは、コードのクリティカル領域でルード スレッドの中止が発生したときに実行されるポリシーのアクションを指定できます。|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|ホストは、重大でないコードの領域でルード スレッドの中止が発生したときに実行されるポリシーのアクションを指定できます。|  
  
## <a name="remarks"></a>Remarks  
 共通言語ランタイム (CLR) の信頼性インフラストラクチャは、中止とリソース内のコードとコードの非クリティカル領域で発生した重要な領域の割り当てエラーを区別します。 この区別は、ホスト コードに障害が発生した場所に応じて異なるポリシーを設定できるように設計されています。  
  
 A*コードのクリティカル領域*は CLR がそのタスクを中止またはをリソースは、現在のタスクのみに影響を与えるは、要求を完了できない状態を保証できない領域。 たとえば、タスクは、ロックが保持するいると、メモリの割り当て要求時にエラーを示す HRESULT を受け取るはの安定性を確保するには、そのタスクを中止するだけでは不十分、<xref:System.AppDomain>ため、<xref:System.AppDomain>他を含めることができますタスクが同じロックを待っています。 現在を破棄する可能性がありますタスクがタスクの他の応答を停止する (またはハング) する無限にします。 このような場合は、全体をアンロードする機能、ホストする必要があります。<xref:System.AppDomain>リスクの潜在的なが不安定になるのではなく。  
  
 A*コードの領域が重大でない*CLR が中断または障害の影響が、エラーが発生しているタスクだけことを保証できるリージョンは、その一方で、します。  
  
 CLR は、グレースフルと非グレースフル (ルード) 中止間も区別します。 一般に、正常または適切な中止は、ルード中止はこのような保証をいたしません中にタスクを中止する前に、例外処理ルーチンとファイナライザーを実行するよう努力します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [EClrFailure 列挙型](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction 列挙型](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
