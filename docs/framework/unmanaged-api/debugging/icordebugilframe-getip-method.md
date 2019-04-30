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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a7b8985e7580282d0e38205f9b1d6078f86cee6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988612"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP メソッド
命令ポインターの値と命令ポインターの値の取得方法を示すビットごとの組み合わせ値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pnOffset`  
 [out]命令ポインターの値。  
  
 `pMappingResult`  
 [out]命令ポインターの値の取得方法を説明する CorDebugMappingResult 列挙値のビットごとの組み合わせへのポインター。  
  
## <a name="remarks"></a>Remarks  
 命令ポインターの値は、関数の Microsoft intermediate language (MSIL) コードにスタック フレームのオフセットです。 スタック フレームがアクティブな場合は、このアドレスは次の命令を実行するには。 スタック フレームがアクティブでない場合、このアドレスは、スタック フレームが再アクティブ化したときに実行するには、次の命令は。  
  
 このフレームが・ イン タイム (JIT) コンパイルされたフレームの場合は、命令ポインターの値は値が概数のみであるため、実際のネイティブ命令ポインターから旧バージョンとのマッピングで決定します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
