---
title: IHostIoCompletionManager::GetHostOverlappedSize メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c43f906961b9e76d5f0f34ba5a5b2f656f5b1488
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937515"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize メソッド
ホストが i/o 要求に追加しようとしているカスタムデータのサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pcbSize`  
 入出力Win32 `OVERLAPPED`オブジェクトのサイズに加えて、共通言語ランタイム (CLR: common language runtime) によって割り当てられるバイト数へのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize`正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドから E_FAIL が返された場合、そのプロセス内で CLR は使用できなくなります。 後続のホストメソッドの呼び出しでは、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 Windows プラットフォーム api に対するすべての非同期 i/o 呼び出しは、ファイル`OVERLAPPED`ポインターの位置などの情報を提供する Win32 オブジェクトを受け取ります。 状態を維持するために、非同期 i/o 呼び出しを行うアプリケーションは、通常、カスタムデータを構造に追加します。 `GetHostOverlappedSize`と[Iho、O補完 manager:: InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)は、このようなカスタムデータをホストに含める機会を提供します。  
  
 CLR は、 `GetHostOverlappedSize`メソッドを呼び出して、ホストが`OVERLAPPED`オブジェクトに追加するカスタムデータのサイズを決定します。  
  
> [!NOTE]
> `GetHostOverlappedSize`は1回だけ呼び出されます。 ホストのカスタムデータは、すべての i/o 要求に対して同じサイズである必要があります。  
  
> [!IMPORTANT]
> `OVERLAPPED`オブジェクト自体のサイズは、の`pcbSize`値には含まれません。  
  
 構造体の`OVERLAPPED`詳細については、Windows プラットフォームのドキュメントを参照してください。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Threading.NativeOverlapped>
- [ICLRIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
