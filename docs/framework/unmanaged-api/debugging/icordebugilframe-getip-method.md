---
title: ICorDebugILFrame::GetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178824"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP メソッド
命令ポインターの値と、命令ポインターの値がどのように取得されたかを記述するビットごとの組み合わせ値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pnOffset`  
 [アウト]命令ポインターの値。  
  
 `pMappingResult`  
 [アウト]命令ポインターの値が取得された方法を記述する、CorDebugMappingResult 列挙値のビットごとの組み合わせへのポインター。  
  
## <a name="remarks"></a>解説  
 命令ポインターの値は、スタック フレームの関数の Microsoft 中間言語 (MSIL) コードへのオフセットです。 スタック フレームがアクティブな場合、このアドレスが次に実行される命令になります。 スタック フレームがアクティブでない場合、このアドレスはスタック フレームが再アクティブ化されたときに実行される次の命令です。  
  
 このフレームがジャスト イン タイム (JIT) コンパイルされたフレームの場合、命令ポインターの値は実際のネイティブ命令ポインターから逆方向にマッピングすることによって決定されるため、値は概算値に過ぎない可能性があります。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
