---
title: InitDbgTransportManager 関数
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948e97064d12dc5b2044faf35aa374e5ba5f2592
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764782"
---
# <a name="initdbgtransportmanager-function"></a>InitDbgTransportManager 関数
プロセスおよびランタイムの列挙のためにリモート ターゲットに接続するよう、トランスポート マネージャーを初期化します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 成功。  
  
 E_OUTOFMEMORY  
 関数はトランスポート マネージャーにメモリを割り当てられませんでした。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 その他のエラーが発生しました。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CoreClrRemoteDebuggingInterfaces.h  
  
 **ライブラリ:** mscordbi_macx86.dll  
  
 **.NET framework のバージョン:** 3.5 SP1
