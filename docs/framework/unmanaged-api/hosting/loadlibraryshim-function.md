---
title: LoadLibraryShim 関数
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32aee404891bfad1aed2abc9ad84e43bcd002df5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765324"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim 関数
指定したバージョンの .NET Framework 再頒布可能パッケージに含まれている DLL を読み込みます。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。 使用して、 [iclrruntimeinfo::loadlibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szDllName`  
 [in].NET Framework ライブラリから読み込まれる DLL の名前を表す、0 で終わる文字列。  
  
 `szVersion`  
 [in]読み込まれる DLL のバージョンを表す、0 で終わる文字列。 場合`szVersion`読み込みはバージョン 4 未満である指定された DLL の最新バージョンを選択したバージョンは null です。 場合は、バージョン 4 以上のすべてのバージョンは無視されます`szVersion`が null の場合と、version 4 より前のバージョンがインストールされていない場合、DLL の読み込みに失敗します。 インストールを確認します。 これは、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]の既存のアプリケーションやコンポーネントには影響しません。 エントリを参照してください。[インプロセス SxS と移行のクイック スタート](https://go.microsoft.com/fwlink/?LinkId=200329)CLR チームのブログにします。  
  
 `pvReserved`  
 将来使用するために予約されています。  
  
 `phModDll`  
 [out]モジュールのハンドルへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値だけでなく、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|CLR_E_SHIM_RUNTIMELOAD|読み込み`szDllName`共通言語ランタイム (CLR) と必要なバージョンの CLR を読み込めません。 読み込む必要があります。|  
  
## <a name="remarks"></a>Remarks  
 この関数は、.NET Framework 再頒布可能パッケージに含まれている Dll の読み込みに使用されます。 ユーザーが生成した Dll は読み込まれません。  
  
> [!NOTE]
>  以降、.NET Framework version 2.0 と、読み込まれる CLR Fusion.dll を読み込むとします。 Fusion.dll で関数が、ラッパーが、この実装は、ランタイムによって提供されるためです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
