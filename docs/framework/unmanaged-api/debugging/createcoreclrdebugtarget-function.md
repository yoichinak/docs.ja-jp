---
title: CreateCoreClrDebugTarget 関数
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: 0b210f105495fa3f5595adbcb0805e1d1fb62310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179216"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget 関数
リモート コンピューターで実行されているデバッガー プロキシへの接続を作成し、リモート コンピューター上で実行中のプロセスと読み込まれたランタイムを照会するために使用できる[ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)オブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwAddress`  
 [in] リモート対象コンピューターの IPv4 アドレス。  
  
 `ppTarget`  
 [アウト]作成される[オブジェクト](icoreclrdebugtarget-interface.md)へのポインター。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 プロセス内の CLR 数が正常に判別され、対応するハンドルとパスの配列が正しく入力されました。  
  
 E_OUTOFMEMORY  
 `ppTarget`  用に十分なメモリを割り当てることができません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 その他のエラーが発生しました。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** インターフェイスを使用します。  
  
 **ライブラリ:** mscordbi_macx86.dll  
  
 **.NET フレームワークのバージョン:** 3.5 SP1
