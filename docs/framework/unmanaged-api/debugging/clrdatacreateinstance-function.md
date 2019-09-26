---
title: CLRDataCreateInstance 関数
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d44f9b5dc42147959d3f1d127a64d39258f515
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274263"
---
# <a name="clrdatacreateinstance-function"></a>CLRDataCreateInstance 関数
指定したターゲット項目のインターフェイスオブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `iid`  
 からインスタンス化するインターフェイスの識別子。  
  
 `target`  
 からインターフェイスオブジェクトの作成対象となる項目を表す、ユーザーによって実装された[ICLRDataTarget](iclrdatatarget-interface.md)オブジェクトへのポインター。  
  
 `iface`  
 入出力返されたインターフェイスオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 `ICLRDataTarget`オブジェクトは、デバッグアプリケーションのライターによって実装されます。 実装は、表示されるターゲット項目の種類によって異なります。 ターゲット項目には、プロセス、メモリダンプ、リモートコンピューターなどがあります。  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** ClrData .idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ グローバル静的関数](debugging-global-static-functions.md)
