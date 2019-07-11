---
title: ICorDebugThread::EnumerateChains メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f0ed843f72d3f1e1575da15776a94a9097fd02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771103"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains メソッド
この ICorDebugThread オブジェクト内のすべてのスタック チェーンを含む ICorDebugChainEnum 列挙子へのインターフェイス ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppChains`  
 [out]アドレスへのポインター、`ICorDebugChainEnum`アクティブ (つまり、最も最近) チェーンから始まる、このスレッド内のチェーンをすべてのスタックの列挙を許可するオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 スタック チェーンでは、スレッドの物理呼び出し履歴を表します。 次の状況では、スタック チェーンの境界を作成します。  
  
- マネージとアンマネージまたはアンマネージからマネージへの移行。  
  
- コンテキストの切り替え。  
  
- A のユーザー スレッドのハイジャックのデバッガーです。  
  
 純粋なマネージ コードを 1 つのコンテキストで実行しているスレッドの単純な場合は、1 対 1 の対応はスレッドとスタック チェーンの間存在します。  
  
 デバッガーは、論理呼び出し履歴にすべてのスレッドの物理呼び出し履歴を再配置する場合があります。 これには、すべてのスレッドのチェーンを呼び出し元/呼び出し先のリレーションシップによって並べ替えられ、それらが含まれます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
