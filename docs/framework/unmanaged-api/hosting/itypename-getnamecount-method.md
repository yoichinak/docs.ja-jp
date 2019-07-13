---
title: ITypeName::GetNameCount メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetNameCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetNameCount
helpviewer_keywords:
- GetNameCount method [.NET Framework hosting]
- ITypeName::GetNameCount method [.NET Framework hosting]
ms.assetid: 0beb909a-5095-40e5-909d-9ecc280300b8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 776af3db0a1d50e56e679fe50a99f620c281f06e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748965"
---
# <a name="itypenamegetnamecount-method"></a>ITypeName::GetNameCount メソッド
このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNameCount (  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
