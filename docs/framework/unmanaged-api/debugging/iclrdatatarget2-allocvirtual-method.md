---
title: ICLRDataTarget2::AllocVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ba9200419d6b6fef467ae02bd74101414e125da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698006"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual メソッド
このターゲット プロセスのアドレス空間でメモリの割り当てに共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `addr`  
 [in]A`CLRDATA_ADDRESS`割り当てられるメモリの要求の開始アドレスを指定する値。  
  
 `size`  
 [in]割り当てられるメモリのバイト単位のサイズ。  
  
 `typeFlags`  
 [in]メモリの割り当てを制御するフラグ。 Win32 を参照してください。`VirtualAlloc`関数。  
  
 `protectFlags`  
 [in]割り当てられたメモリの保護属性。 Win32 を参照してください。`VirtualAlloc`関数。  
  
 `virt`  
 [out]ポインターを`CLRDATA_ADDRESS`割り当てられたメモリの実際の開始アドレスを指定する値。  
  
## <a name="remarks"></a>Remarks  
 `AllocVirtual`メソッドは、Win32 の論理ラッパーとして機能`VirtualAlloc`関数。  
  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [FreeVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
