---
title: ICLRDataTarget2::FreeVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: c084a3fcbbc02504124a511c6e136be32f408d21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112325"
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual メソッド
ターゲットプロセスのアドレス空間で以前に割り当てられたメモリを解放するために、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `addr`  
 から解放されるメモリの開始アドレスを指定する `CLRDATA_ADDRESS` 値。  
  
 `size`  
 から解放されるメモリのサイズ (バイト単位)。  
  
 `typeFlags`  
 からメモリの解放を制御するフラグ。 Win32 `VirtualFree` 関数を参照してください。  
  
## <a name="remarks"></a>Remarks  
 `FreeVirtual` メソッドは、Win32 `VirtualFree` 関数の論理ラッパーとして機能します。  
  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [AllocVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
