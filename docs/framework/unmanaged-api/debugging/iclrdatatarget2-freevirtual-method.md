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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b30bd3e97af8d222f629c5b4f9f318a9b6379e78
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181403"
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual メソッド
ターゲット プロセスのアドレス空間に割り当てられていたメモリを解放共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `addr`  
 [in]A`CLRDATA_ADDRESS`が解放されるメモリの開始アドレスを指定する値。  
  
 `size`  
 [in]解放するメモリのバイト単位のサイズ。  
  
 `typeFlags`  
 [in]メモリの解放を制御するフラグ。 Win32 を参照してください。`VirtualFree`関数。  
  
## <a name="remarks"></a>Remarks  
 `FreeVirtual`メソッドは、Win32 の論理ラッパーとして機能`VirtualFree`関数。  
  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [AllocVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
