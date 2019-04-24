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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed3cb62b56e80a7fe4ea54b43ac9f4a28b8d102
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100250"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget インターフェイス
共通言語ランタイム (CLR) のターゲット項目と対話するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCurrentThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|現在のスレッドのオペレーティング システムの識別子を取得します。|  
|[GetImageBase メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|指定したイメージのメモリのベース アドレスを取得します。|  
|[GetMachineType メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|ターゲット プロセスを使用している命令セットの種類の識別子を取得します。|  
|[GetPointerSize メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|現在のターゲットへのポインターのバイト単位のサイズを取得します。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|指定した識別子、スレッドのコンテキストへのポインターを取得します。|  
|[GetTLSValue メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|スレッド ローカル ストレージ (TLS) で指定されたスレッドの指定したインデックス位置の値を取得します。|  
|[ReadVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|指定されたバッファーに指定された仮想メモリ アドレスからのデータを読み取ります。|  
|[Request メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|実装によって定義されているように、操作を要求する共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。|  
|[SetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|ターゲット プロセスでは、指定したスレッドの現在のコンテキストを設定します。|  
|[SetTLSValue メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|ターゲット プロセス内の指定したスレッドのスレッド ローカル ストレージ (TLS) の値を設定します。|  
|[WriteVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|指定された仮想メモリ アドレスには、指定したバッファーからデータを書き込みます。|  
  
## <a name="remarks"></a>Remarks  
 API クライアント (つまりデバッガー) は、特定のターゲット項目に適したには、このインターフェイスを実装する必要があります。 たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
