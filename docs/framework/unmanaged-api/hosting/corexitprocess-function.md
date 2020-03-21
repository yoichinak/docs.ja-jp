---
title: CorExitProcess 関数
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: 44578595b3cb790570c5359e714bd39c109cf1f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176462"
---
# <a name="corexitprocess-function"></a>CorExitProcess 関数
現在のアンマネージ プロセスを終了します。  
  
 この関数は、.NET Framework 4 では廃止されました。 代わりにメソッドを使用[します](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `exitCode`  
 プロセス終了コードを指定する整数。  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> .NET Framework 4 以降`CorExitProcess`では、従来の API がバインドされているランタイムだけでなく、プロセス内で開始されたすべてのランタイムを終了します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
