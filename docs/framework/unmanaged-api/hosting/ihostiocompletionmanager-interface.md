---
title: IHostIoCompletionManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c3bebe8eabd4d5fd5faec21e0b0efc408353bc2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197270"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager インターフェイス
共通言語ランタイム (CLR) に、ホストによって提供される I/O 完了ポートとやり取りできるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Bind メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|I/O 完了ポートへのハンドルにバインドします。|  
|[CloseIoCompletionPort メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|以前の呼び出しを使用して作成されたポートを閉じる`CreateIoCompletionPort`します。|  
|[CreateIoCompletionPort メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|ホストが新しい I/O 完了ポートを作成することを要求します。|  
|[GetAvailableThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|現在の要求を処理していない I/O 完了スレッドの数を取得します。|  
|[GetHostOverlappedSize メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|ホストが I/O 要求に追加するカスタム データのサイズを取得します。|  
|[GetMaxThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|I/O 要求を処理するには、ホストに割り当てることができますのスレッドの最大数を取得します。|  
|[GetMinThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|I/O 要求を処理するには、ホストを提供するスレッドの最小数を取得します。|  
|[InitializeHostOverlapped メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|ホストを I/O 要求に関するすべてのカスタム データを初期化する機会を提供します。|  
|[SetCLRIoCompletionManager メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|により、ホストへのインターフェイス ポインターで、 [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) CLR で実装されているインスタンス。|  
|[SetMaxThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|I/O 要求を処理するため、ホストに割り当てるスレッドの最大数を設定します。|  
|[SetMinThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|I/O 完了するには、ホストを割り当てるスレッドの最小数を設定します。|  
  
## <a name="remarks"></a>Remarks  
 `IHostIoCompletionManager` 対応する、 `ICLRIoCompletionManager` CLR によって実装されるインターフェイス。 CLR のメソッドを呼び出して、`IHostIoCompletionManager`ハンドルをホストを提供して、ホストのメソッドを呼び出すポートにバインドする`ICLRIoCompletionManager`I/O 要求の完了を報告します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
