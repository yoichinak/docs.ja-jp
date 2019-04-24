---
title: ICLRDebuggingLibraryProvider::ProvideLibrary メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f5d44b6497e971e6d1ed030c043b91b88c070b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218512"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary メソッド
ライブラリのプロバイダーに共通言語ランタイム (CLR) バージョン固有デバッグ ライブラリを検索しに読み込む要求を許可するコールバック インターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwszFilename`  
 [in]要求されているモジュールの名前。  
  
 `dwTimestamp`  
 [in]PE ファイルの COFF ファイル ヘッダーに格納されている日付時刻スタンプ。  
  
 `pLibraryProvider`  
 [in]`SizeOfImage` PE ファイルの COFF 省略可能なファイルのヘッダーに格納されているフィールドです。  
  
 `hModule`  
 [out]要求されたモジュールのハンドルです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 `ProvideLibrary` mscordbi.dll mscordacwks.dll などの特定の CLR ファイルをデバッグするために必要なモジュールを提供するデバッガーを使用します。 呼び出すまで、有効なままのモジュール ハンドルが、 [iclrdebugging::canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)メソッドは、これら解放される可能性があります、この時点では、ハンドルを解放する呼び出し元の責任のことを示します。  
  
 デバッガーは、検索またはデバッグ モジュールを調達、使用可能な手段を使用できます。  
  
> [!IMPORTANT]
>  この機能は、実行可能ファイル、および、場合によって悪意のあるコードが含まれているモジュールを提供する API の呼び出し元を使用できます。 セキュリティの予防措置として、呼び出し元を使用する必要がありますいない`ProvideLibrary`自体を実行するつもりはないすべてのコードを配布します。  
>   
>  Mscordbi.dll または mscordacwks.dll などのリリース済みのライブラリで重大なセキュリティ上の問題が検出された場合、shim パッチを適用できるファイルの不適切なバージョンを認識します。 Shim のパッチが適用されたバージョンのファイルの要求を発行し、すべての要求に対する応答で提供される場合は、不適切なバージョンを拒否します。 これは、ユーザーが、shim の新しいバージョンにパッチを適用する場合にのみに発生します。 未適用のバージョンは、脆弱なままです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
