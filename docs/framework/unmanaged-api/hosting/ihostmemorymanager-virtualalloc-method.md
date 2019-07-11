---
title: IHostMemoryManager::VirtualAlloc メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a0764cb212a95412a4dcf9455b7648ee863951e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767663"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc メソッド
対応する Win32 関数の論理ラッパーとして機能します。 Win32 実装`VirtualAlloc`予約または呼び出し元のプロセス仮想アドレス空間内のページの領域をコミットします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAddress`  
 [in]割り当てる領域の開始アドレスへのポインター。  
  
 `dwSize`  
 [in]リージョンのバイト単位のサイズ。  
  
 `flAllocationType`  
 [in]メモリ割り当ての種類。  
  
 `flProtect`  
 [in]割り当てられるページの領域のメモリ保護します。  
  
 `dwCriticalLevel`  
 [in][EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)割り当てエラーの影響を示す値。  
  
 `ppMem`  
 [out]割り当てられたメモリは、または要求を処理できなかった場合は null の開始アドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_OUTOFMEMORY|十分なメモリが割り当て要求を完了できませんでした。|  
  
## <a name="remarks"></a>Remarks  
 呼び出すことによって、プロセスのアドレス空間で領域を予約する`VirtualAlloc`します。 `pAddress`パラメーターにするメモリ ブロックの開始アドレスが含まれています。 このパラメーターの設定は、通常 null にします。 オペレーティング システムをプロセスに使用可能な無料のアドレス範囲のレコードを保持します。 A`pAddress`値は null ですが、システムに最適と思われる任意の場所に領域を予約するように指示します。 また、メモリ ブロックの特定の開始アドレスを行うことができます。 どちらの場合も、出力パラメーター`ppMem`が割り当てられたメモリへのポインターとして返されます。 関数自体では、HRESULT 値を返します。  
  
 Win32`VirtualAlloc`関数はありません、`ppMem`パラメーターと、代わりに、割り当てられたメモリへのポインターを返します。 詳細については、Windows プラットフォームのドキュメントを参照してください。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
