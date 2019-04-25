---
title: ICLRDebugManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22c3a480e2b68377e300df1083b3178ee4e2d2a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198843"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager インターフェイス
Id とフレンドリ名を関連付ける一連のタスクをホストできるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BeginConnection メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|ホストとデバッガーは、id とフレンドリ名を関連付けるタスクの間の新しい接続を確立します。|  
|[EndConnection メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|タスクの一覧と、識別子とフレンドリ名の間の関連付けを削除します。|  
|[GetDacl メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|このメソッドは実装されていません。|  
|[IsDebuggerAttached メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|デバッガーがプロセスにアタッチされているかどうかを示す値を取得します。|  
|[SetConnectionTasks メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|リストを関連付けます[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)識別子とフレンドリ名を持つインスタンス。|  
|[SetDacl メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|このメソッドは実装されていません。|  
|[SetSymbolReadingPolicy メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|プログラム データベース (PDB) ファイルを読み取るためのポリシーを設定します。 ポリシーは、呼び出し履歴で行番号およびファイルに関する情報が含まれているかどうかを判断します。|  
  
## <a name="remarks"></a>Remarks  
 シナリオをデバッグするには、ホストは、独自のプログラミング ロジックに従ってタスクをグループ化をする可能性があります。 たとえばをグループ化は、開発者は、プロセスで実行されているすべてのタスクではなく、開発者の Api で必要なタスクのみを参照してください。 `ICLRDebugManager` この種のグループ化を実装するためにホストできるようにします。  
  
> [!IMPORTANT]
>  次の 3 つ`ICLRDebugManager`メソッド、 `BeginConnection`、`SetConnectionTasks`と`EndConnection`、互いに依存します。 期待どおりに動作する特定の順序で呼び出す必要があります。  
  
 グループ化、および識別子とホストは、グループに割り当てます。 フレンドリ名ありませんにとって意味のある共通言語ランタイム (CLR)。 CLR は、デバッガーを利用して、情報を渡すだけです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
