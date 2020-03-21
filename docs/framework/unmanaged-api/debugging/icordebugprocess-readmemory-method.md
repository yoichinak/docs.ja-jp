---
title: ICorDebugProcess::ReadMemory メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178663"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory メソッド
このプロセスのメモリの指定された領域を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 [in]読`CORDB_ADDRESS`み取るメモリのベース アドレスを指定する値。  
  
 `size`  
 [in]メモリから読み取るバイト数。  
  
 `buffer`  
 [アウト]メモリの内容を受け取るバッファ。  
  
 `read`  
 [アウト]指定したバッファーに転送されるバイト数へのポインター。  
  
## <a name="remarks"></a>解説  
 この`ReadMemory`メソッドは、主に、デバッグ対象のアンマネージ部分で使用されているメモリ領域を調べるための相互運用機能デバッグで使用されることを目的としています。 このメソッドは、Microsoft 中間言語 (MSIL) コードおよびネイティブ JIT コンパイルコードを読み取るためにも使用できます。  
  
 マネージ ブレークポイントは、`buffer`パラメーターで返されるデータから削除されます。 [ICorDebugProcess2](icordebugprocess2-setunmanagedbreakpoint-method.md)によって設定されたネイティブ ブレークポイントに対する調整は行いません。  
  
 プロセス メモリのキャッシュは実行されません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
