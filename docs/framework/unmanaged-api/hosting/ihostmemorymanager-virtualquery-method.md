---
title: IHostMemoryManager::VirtualQuery メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 028ca0b9cb917d3e6cc0242cbc8c3f4a5a19ab39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760104"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery メソッド
対応する Win32 関数の論理ラッパーとして機能します。 Win32 実装`VirtualQuery`呼び出し元のプロセス仮想アドレス空間内のページの範囲に関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `lpAddress`  
 [in]クエリを実行する仮想メモリ アドレスへのポインター。  
  
 `lpBuffer`  
 [out]指定したメモリ領域に関する情報を格納する構造体へのポインター。  
  
 `dwLength`  
 [in]バッファーのバイト単位のサイズを`lpBuffer`を指します。  
  
 `pResult`  
 [out]情報バッファーによって返されたバイト数へのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`VirtualQuery` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 `VirtualQuery` 呼び出し元のプロセス仮想アドレス空間内のページの範囲について説明します。 この実装の値の設定、`pResult`バイト数のパラメーター情報バッファーに返され、HRESULT 値を返します。 Win32 で`VirtualQuery`関数、戻り値は、バッファー サイズ。 詳細については、Windows プラットフォームのドキュメントを参照してください。  
  
> [!IMPORTANT]
>  オペレーティング システムの実装の`VirtualQuery`デッドロックは発生しませんし、ユーザー コードで中断されているランダムなスレッドで完了するまで実行できます。 このメソッドのホストされたバージョンを実装する場合は、注意を使用します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
