---
title: ICorDebugCode3::GetReturnValueLiveOffset メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f1f4734b6cb5b214b219742a6cac1c50220b96e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492856"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset メソッド
指定した IL オフセットについて、デバッガーが関数からの戻り値を取得できるように、ブレークポイントを配置する必要があるネイティブなオフセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ILoffset`  
 オフセット IL。 関数呼び出しサイトであることが必要です。そうでない場合、関数呼び出しは失敗します。  
  
 `bufferSize`  
 
  `pOffsets` を格納できるバイト数。  
  
 `pFetched`  
 実際に返されたオフセットの数へのポインター。 通常、この値は 1 ですが、単一の IL 命令が複数の `CALL` アセンブリ命令にマップする場合があります。  
  
 `pOffsets`  
 ネイティブ オフセットの配列。 通常、`pOffsets` には単一のオフセットが含まれますが、単一の IL 命令が複数の `CALL` アセンブリ命令に対する複数のマップに対応する場合があります。  
  
## <a name="remarks"></a>Remarks  
 このメソッドはと共に使用、 [icordebugilframe 3::getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)参照型を返すメソッドの戻り値を取得します。 関数呼び出しサイトに対する IL オフセットをこのメソッドに渡すと、1 つ以上のネイティブ オフセットが返されます。 これによってデバッガーは、関数内のこうしたネイティブ オフセット上でブレークポイントを設定できます。 このメソッドに渡した同じ IL オフセットを渡すことができますし、デバッガーのブレークポイントのいずれかが発生すると、 [icordebugilframe 3::getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)戻り値を取得します。 この場合、デバッガーは設定したブレークポイントすべてをクリアする必要があります。  
  
> [!WARNING]
>  `ICorDebugCode3::GetReturnValueLiveOffset`と[icordebugilframe 3::getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)メソッドでは、参照型だけの戻り値の情報を取得できます。 値型 (つまり、<xref:System.ValueType> から派生するすべての型) からの戻り値情報の取得はサポートされません。  
  
 この関数は、次の表に示す `HRESULT` 値を返します。  
  
|`HRESULT` の値|説明|  
|---------------------|-----------------|  
|`S_OK`|成功。|  
|`CORDBG_E_INVALID_OPCODE`|指定した IL オフセット サイトが呼び出し命令ではないか、関数が `void` を返しています。|  
|`CORDBG_E_UNSUPPORTED`|指定した IL オフセットは適切な呼び出しですが、取得する戻り値の型がサポートされていません。|  
  
 
  `ICorDebugCode3::GetReturnValueLiveOffset` メソッドは、x86 ベースおよび AMD64 システムでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [GetReturnValueForILOffSet メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
