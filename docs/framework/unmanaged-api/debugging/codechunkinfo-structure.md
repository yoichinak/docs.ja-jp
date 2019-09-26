---
title: CodeChunkInfo 構造体
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36afee8af3de046683c55215a677a529b0837c77
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274255"
---
# <a name="codechunkinfo-structure"></a>CodeChunkInfo 構造体

メモリ内のコードの単一のチャンクを表しています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`startAddr`|チャンクの開始アドレスを示す値です。`CORDB_ADDRESS`|  
|`length`|チャンクのサイズ (バイト単位)。|  
  
## <a name="remarks"></a>コメント  
 コードの1つのチャンクは、関数などのコードオブジェクトの一部であるネイティブコードの領域です。  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetCodeChunks メソッド](icordebugcode2-getcodechunks-method.md)
- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
