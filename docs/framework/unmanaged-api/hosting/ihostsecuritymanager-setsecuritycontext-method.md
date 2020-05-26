---
title: IHostSecurityManager::SetSecurityContext メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
ms.openlocfilehash: 79ef08ef70ad1132ceacc3e2b997651e57032b9a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803811"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a>IHostSecurityManager::SetSecurityContext メソッド
現在実行中のスレッドのセキュリティコンテキストを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `eContextType`  
 から[EContextType](econtexttype-enumeration.md)値の1つ。共通言語ランタイム (CLR) がホストに配置しているコンテキストの種類を示します。  
  
 `ppSecurityContext`  
 入出力新しい[IHostSecurityContext](ihostsecuritycontext-interface.md)オブジェクトのアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`SetSecurityContext`正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。 後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>解説  
 CLR は `SetSecurityContext` いくつかのシナリオでを呼び出します。 CLR は、クラスコンストラクターとモジュールコンストラクター、およびファイナライザーを実行する前にを呼び出して、 `SetSecurityContext` ホストが実行エラーから保護されるようにします。 次に、への別の呼び出しを使用して、コンストラクターまたはファイナライザーの実行後に、セキュリティコンテキストを元の状態にリセットし `SetSecurityContext` ます。 同様のパターンは、i/o の完了時に発生します。 ホストが[Ihostiocompletionmanager manager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)を実装している場合、CLR は `SetSecurityContext` ホストが[Iclriocomplete Manager:: oncomplete](iclriocompletionmanager-oncomplete-method.md)を呼び出した後にを呼び出します。  
  
 ワーカースレッドの非同期ポイントでは、CLR は `SetSecurityContext` 、 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ホストまたは clr がスレッドプールを実装しているかどうかに応じて、 [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md)内または内でを呼び出します。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [EContextType 列挙型](econtexttype-enumeration.md)
- [ICLRIoCompletionManager インターフェイス](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager インターフェイス](ihostiocompletionmanager-interface.md)
- [IHostSecurityContext インターフェイス](ihostsecuritycontext-interface.md)
- [IHostSecurityManager インターフェイス](ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager インターフェイス](ihostthreadpoolmanager-interface.md)
