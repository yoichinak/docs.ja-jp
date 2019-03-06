---
title: IHostMemoryManager::NeedsVirtualAddressSpace メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fe47a155b29fe452a59adfaffe59162f60f58aa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469575"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>IHostMemoryManager::NeedsVirtualAddressSpace メソッド
共通言語ランタイム (CLR) が指定されたメモリを使用しようとしています。 しようとしていることをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `startAddress`  
 [in]メモリの開始アドレス。  
  
 `size`  
 [in]メモリのバイト単位のサイズ。  
  
## <a name="remarks"></a>Remarks  
 `NeedsVirtualAddressSpace`メソッドは、コールバック メソッドであり、ホスト アプリケーションの作成者によって実装する必要があります。 CLR によって呼び出されます。  
  
 ホストが指定されたメモリを使用する CLR をしない場合は、E_OUTOFMEMORY HRESULT が返される可能性があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
