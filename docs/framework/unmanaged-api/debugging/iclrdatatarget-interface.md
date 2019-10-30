---
title: ICLRDataTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: 51b246e45b8bbdf809f5e90ac2bc29ca724751fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113491"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget インターフェイス
共通言語ランタイム (CLR) のターゲット項目と対話するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCurrentThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|現在のスレッドのオペレーティングシステム id を取得します。|  
|[GetImageBase メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|指定したイメージのベースメモリアドレスを取得します。|  
|[GetMachineType メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|ターゲットプロセスが使用している命令セットの種類の識別子を取得します。|  
|[GetPointerSize メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|現在のターゲットへのポインターのサイズ (バイト単位) を取得します。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|指定した識別子を持つスレッドのコンテキストへのポインターを取得します。|  
|[GetTLSValue メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|指定したスレッドの指定したインデックスにあるスレッドローカルストレージ (TLS) の値を取得します。|  
|[ReadVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|指定された仮想メモリアドレスから指定されたバッファーにデータを読み取ります。|  
|[Request メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|実装で定義されているように、操作を要求するために、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。|  
|[SetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|ターゲットプロセス内の指定されたスレッドの現在のコンテキストを設定します。|  
|[SetTLSValue メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|ターゲットプロセス内の指定したスレッドのスレッドローカルストレージ (TLS) の値を設定します。|  
|[WriteVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|指定されたバッファーから指定された仮想メモリアドレスにデータを書き込みます。|  
  
## <a name="remarks"></a>Remarks  
 API クライアント (つまり、デバッガー) は、特定のターゲット項目に適した方法でこのインターフェイスを実装する必要があります。 たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
