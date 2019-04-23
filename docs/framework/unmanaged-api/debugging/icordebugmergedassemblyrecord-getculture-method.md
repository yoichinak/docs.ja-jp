---
title: Icordebugmergedassemblyrecord::getculture メソッド
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 093b21a439b96c9fe2f971300f314d1b75527f1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207202"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>Icordebugmergedassemblyrecord::getculture メソッド
アセンブリのカルチャ名文字列を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cchCulture`  
 [in] `szCulture` バッファー内の文字数。  
  
 `pcchCulture`  
 [out] `szCulture` バッファーに実際に書き込まれた文字数。  
  
 `szCulture`  
 [out] カルチャ名を格納する文字配列。  
  
## <a name="remarks"></a>Remarks  
 カルチャ名は、"en-US" (英語 (米国) カルチャ)、"neutral" (ニュートラル カルチャ) など、カルチャを識別する一意の文字列です。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMergedAssemblyRecord インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
