---
title: COR_VERSION 構造体
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffbe571ebc3d14c12e57b1f805d77e56e97d12e1
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274181"
---
# <a name="cor_version-structure"></a>COR_VERSION 構造体
共通言語ランタイムの標準の 4 つの部分のバージョン番号を保存します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`dwMajor`|メジャー バージョン番号。|  
|`dwMinor`|マイナー バージョン番号。|  
|`dwBuild`|ビルド番号。|  
|`dwSubBuild`|サブビルド番号。|  
  
## <a name="remarks"></a>コメント  
 バージョン番号が1.0.3705.288 の場合、1はメジャーバージョン番号、0はマイナーバージョン番号、3705はビルド番号、288はサブビルド番号です。  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
