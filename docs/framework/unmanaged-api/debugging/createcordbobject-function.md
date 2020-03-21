---
title: CreateCordbObject 関数
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179227"
---
# <a name="createcordbobject-function"></a>CreateCordbObject 関数
リモート プロセスでマネージ デバッグ セッションをインスタンス化するための機能を提供するデバッガー インターフェイス ([ICorDebug](icordebug-interface.md)) を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `iDebuggerVersion`  
 [in] ターゲット プロセスのデバッガー バージョン。 リモート デバッグの場合、このパラメーターは CorDebugVersion_2_0 である必要があります。  
  
 `ppCordb`  
 [アウト][ICorDebug](icordebug-interface.md)インターフェイスにキャストされ、返されるオブジェクトへのポインターへのポインター。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 プロセス内の CLR 数が正常に判別され、対応するハンドルとパスの配列が正しく入力されました。  
  
 E_INVALIDARG  
 `ppCordb` が null であるか、または `iDebuggerVersion` が CorDebugVersion_2_0 ではありません。  
  
 E_OUTOFMEMORY  
 `ppCordb` 用に十分なメモリを割り当てることができません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 その他のエラーが発生しました。  
  
## <a name="remarks"></a>解説  
 返される[ICorDebug](icordebug-interface.md)インターフェイス`ppCordb`は、すべてのマネージ デバッグ サービスのトップレベルのデバッグ インターフェイスです。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** インターフェイスを使用します。  
  
 **ライブラリ:** mscordbi_macx86.dll  
  
 **.NET フレームワークのバージョン:** 3.5 SP1
