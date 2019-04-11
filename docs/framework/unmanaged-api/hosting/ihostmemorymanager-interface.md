---
title: IHostMemoryManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57f34ed1796f6fa411d31fca83baeff693f85d70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137359"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager インターフェイス
Win32 仮想メモリの標準の関数を使用する代わりに、共通言語ランタイム (CLR) を通じて、ホストの仮想メモリの要求を行うことができるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|共通言語ランタイム (CLR) が、オペレーティング システムから指定されたメモリが獲得されるホストに通知します。|  
|[CreateMAlloc メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|インターフェイス ポインターを取得、 [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)ホストによって作成されたヒープからメモリの割り当てを要求するために使用するインスタンス。|  
|[GetMemoryLoad メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|ホストによって報告された、現在使用されている物理メモリの量を取得します。|  
|[NeedsVirtualAddressSpace メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|CLR が指定されたメモリを使用しようとしています。 しようとしていることをホストに通知します。|  
|[RegisterMemoryNotificationCallback メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|ホストが、コンピューター上の現在のメモリ負荷の CLR に通知するために呼び出すコールバック関数へのポインターを登録します。|  
|[ReleasedVirtualAddressSpace メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|指定されたメモリを使用して、CLR が完了したことをホストに通知します。|  
|[VirtualAlloc メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|予約またはコミットの呼び出し元のプロセス仮想アドレス空間内のページの領域、対応する Win32 関数の論理ラッパーとして機能します。|  
|[VirtualFree メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|対応する Win32 関数の解放、デコミット、または解放され、呼び出し元のプロセス仮想アドレス空間内のページの領域をデコミットの論理ラッパーとして機能します。|  
|[VirtualProtect メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|対応する Win32 関数の呼び出し元のプロセス仮想アドレス空間内のコミットされたページの領域で、保護を変更する論理ラッパーとして機能します。|  
|[VirtualQuery メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|対応する Win32 関数の呼び出し元のプロセス仮想アドレス空間内のページの範囲に関する情報を取得する論理ラッパーとして機能します。|  
  
## <a name="remarks"></a>Remarks  
 `IHostMemoryManager` また CLR ホストによって報告されたヒープのメモリ要求を行うと、プロセスのメモリ不足のレベルを取得するためのポインターを取得するためのメソッドを提供します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostMalloc インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
