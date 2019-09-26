---
title: COR_IL_MAP 構造体
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ae4c5743b01c4a9087323678d315473631cb32f
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274049"
---
# <a name="cor_il_map-structure"></a>COR_IL_MAP 構造体
機能の相対オフセットでの変更を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`oldOffset`|関数の先頭を基準とした、以前の Microsoft 中間言語 (MSIL) オフセット。|  
|`newOffset`|関数の先頭を基準とする新しい MSIL オフセット。|  
|`fAccurate`|`true`マッピングが正確であることがわかっている場合は。それ以外`false`の場合は。|  
  
## <a name="remarks"></a>コメント  
 マップの形式は次のとおりです。デバッガーは、が元`oldOffset`の変更されていない msil コード内の msil オフセットを参照することを前提としています。 パラメーター `newOffset`は、新しいインストルメント化されたコード内で、対応する MSIL オフセットを参照します。  
  
 ステップ実行を正常に行うには、次の要件を満たしている必要があります。  
  
- マップは昇順に並べ替える必要があります。  
  
- インストルメント化された MSIL コードを並べ替えることはできません。  
  
- 元の MSIL コードは削除しないでください。  
  
- マップには、プログラムデータベース (PDB) ファイルのすべてのシーケンスポイントをマップするためのエントリが含まれている必要があります。  
  
 マップでは、不足しているエントリは補間されません。 次の例は、マップとその結果を示しています。  
  
 付け  
  
- 0個の古いオフセット、0個の新しいオフセット  
  
- 5個の古いオフセット、10個の新しいオフセット  
  
- 9個の古いオフセット、20個の新しいオフセット  
  
 生じ  
  
- 0、1、2、3、または4の古いオフセットは、新しいオフセット0にマップされます。  
  
- 古いオフセット5、6、7、または8は、新しいオフセット10にマップされます。  
  
- 9以上の古いオフセットは、新しいオフセット20にマップされます。  
  
- 新しいオフセット0、1、2、3、4、5、6、7、8、または9が古いオフセット0にマップされます。  
  
- 新しいオフセット10、11、12、13、14、15、16、17、18、19は、古いオフセット5にマップされます。  
  
- 20以上の新しいオフセットは、古いオフセット9にマップされます。  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、Corprof.idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
