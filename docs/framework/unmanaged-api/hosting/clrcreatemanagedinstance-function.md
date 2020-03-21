---
title: ClrCreateManagedInstance 関数
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176540"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance 関数
指定したマネージド型のインスタンスを作成します。  
  
 この関数は、.NET Framework 4 では廃止されました。 COM アクティベーションを使用してマネージ型のインスタンスを作成するか、ホストを使用します[(.NET Framework 4 および 4.5 で追加された CLR ホスティング インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)を参照)。  
  
## <a name="syntax"></a>構文  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pTypeName`  
 [in]要求されているインスタンス型の名前へのポインター。  
  
 `riid`  
 [in]要求`IID`されているインスタンス型の。  
  
 `ppObject`  
 [アウト]呼び出し元によって要求されたマネージ型のインスタンスへのポインターへのポインター。  
  
## <a name="remarks"></a>解説  
 共通言語ランタイムは、既にプロセスに読み込まれている必要があります。 たとえば、関数が呼び出される前`ClrCreateManagedInstance`に[、関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)の呼び出しを使用して読み込むことができます。 ランタイムがロードされていない場合は、`ClrCreateManagedInstance`まずランタイムの v1.0.3705 のロードを試みます。 失敗した場合は、最新バージョンのランタイムを読み込もうとします。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
