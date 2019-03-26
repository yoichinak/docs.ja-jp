---
title: ICorDebugMetaDataLocator::GetMetaData メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c787a93ac98a086dfb6218d1b4891de87e0e107d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486994"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData メソッド
デバッガーが要求した操作を完了するために必要となるメタデータが含まれているモジュールの完全パスを返すように、デバッガーに求めます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszImagePath`  
 [in] ファイルの完全パスを表す null で終わる文字列。 完全なパスが使用できない場合、名前とファイルの拡張子 (*filename*.*拡張機能*)。  
  
 `dwImageTimeStamp`  
 [in] イメージの PE ファイル ヘッダーのタイムスタンプ。 このパラメーターは、シンボル サーバーの使用可能性があることができます ([SymSrv](/windows/desktop/debug/using-symsrv)) 参照。  
  
 `dwImageSize`  
 [in] PE ファイル ヘッダーのイメージ サイズ。 このパラメーターは、SymSrv の検索に使用される可能性があります。  
  
 `cchPathBuffer`  
 [in] `wszPathBuffer` の文字数。  
  
 `pcchPathBuffer`  
 [out] `wszPathBuffer` に書き込まれる `WCHAR` の数。  
  
 メソッドが E_NOT_SUFFICIENT_BUFFER を返す場合は、パスを格納するために必要な `WCHAR` の数。  
  
 `wszPathBuffer`  
 [out] 要求されたメタデータを格納するファイルの完全パスが、デバッガーによりコピーされるバッファーへのポインター。  
  
 `ofReadOnly`からフラグ、 [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列挙体を使用して、このファイル内のメタデータへの読み取り専用アクセスを要求します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。 これ以外のエラー HRESULT はすべて、ファイルを取得できないことを示します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。 `wszPathBuffer` にはファイルの完全パスが含まれます。また終端は null です。|  
|E_NOT_SUFFICIENT_BUFFER|`wszPathBuffer` の現在のサイズが十分ではないため、完全パスを保持できません。 この場合、`pcchPathBuffer` に必要な `WCHAR` の数 (終端の null 文字も含む) が格納され、要求されたバッファー サイズで `GetMetaData` がもう一度呼び出されます。|  
  
## <a name="remarks"></a>Remarks  
 `wszImagePath` にダンプのモジュールの完全パスが格納されている場合は、ダンプが収集されたコンピューターからのパスを示しています。 この場所にはファイルが存在しない、または同じ名前の正しくないファイルがパス上に格納されている可能性があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebugThread4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
