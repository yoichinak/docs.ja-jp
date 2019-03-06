---
title: _CorDllMain 関数
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3c529e77cad16f0bde12e34491829b58add17aa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500383"
---
# <a name="cordllmain-function"></a>_CorDllMain 関数
共通言語ランタイム (CLR) を初期化します、DLL アセンブリの CLR ヘッダーでマネージ エントリ ポイントを検索し、実行を開始します。  
  
## <a name="syntax"></a>構文  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `hInst`  
 [in]読み込まれたモジュールのインスタンス ハンドル。  
  
 `dwReason`  
 [in]DLL のエントリ ポイント関数が呼び出される理由を示します。 このパラメーターには、次の値のいずれかを指定できます。DLL_PROCESS_ATTACH、DLL_THREAD_ATTACH、DLL_THREAD_ATTACH、または DLL_PROCESS_DETACH します。 これらの値の説明については、次を参照してください。、`DllMain`プラットフォーム SDK のドキュメント。  
  
 `lpReserved`  
 [in]使用されていません。  
  
## <a name="return-value"></a>戻り値  
 このメソッドが戻る`true`成功と`false`エラーが発生した場合。  
  
## <a name="remarks"></a>Remarks  
 この関数は、DLL アセンブリのオペレーティング システム ローダーによって呼び出されます。 実行可能アセンブリ ローダーの呼び出し、 [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)関数を使用します。  
  
 オペレーティング システム ローダーでは、DLL のファイルで指定されたエントリ ポイントに関係なく、このメソッドを呼び出します。  
  
`_CorDllMain`オペレーティング システム ローダーによって直接呼び出されます。
  
 詳細については、「解説」セクションを参照してください。、 [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)トピック。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
