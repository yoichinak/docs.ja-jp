---
title: ITypeNameBuilder::ToString メソッド
ms.date: 03/30/2017
api_name:
- ITypeNameBuilder.ToString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ToString
helpviewer_keywords:
- ToString method [.NET Framework hosting]
- ITypeNameBuilder::ToString method [.NET Framework hosting]
ms.assetid: 6372aca7-869a-4af6-ba2b-0eb1047ef5c0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4e8237d2841863c73989c34a46da61033e111ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765447"
---
# <a name="itypenamebuildertostring-method"></a>ITypeNameBuilder::ToString メソッド
このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ToString (  
    [out, retval] BSTR* pszStringRepresentation  
);  
```  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
