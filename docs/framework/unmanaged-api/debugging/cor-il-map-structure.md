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
ms.openlocfilehash: 02a7bff021387f615c823b2df96615c1284cb82b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617717"
---
# <a name="corilmap-structure"></a>COR_IL_MAP 構造体
機能の相対オフセットでの変更を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`oldOffset`|古い Microsoft intermediate language (MSIL) 関数の先頭からの相対オフセットします。|  
|`newOffset`|関数の先頭を基準とした新しい MSIL オフセット。|  
|`fAccurate`|`true` 正確であるマッピングがわかっている場合それ以外の場合、`false`します。|  
  
## <a name="remarks"></a>Remarks  
 マップの形式は次のとおりです。デバッガーは仮定`oldOffset`、変更されていない元の MSIL コード内で MSIL オフセットを示します。 `newOffset`パラメーターは、新しい、インストルメント化されたコード内で、対応する MSIL のオフセットを表します。  
  
 適切に機能するステップの場合は、次の要件を満たす必要があります。  
  
- マップは、昇順で並べ替えする必要があります。  
  
- インストルメント化された MSIL コードは並べ替えないでください。  
  
- 元の MSIL コードを削除しない必要があります。  
  
- マップには、プログラム データベース (PDB) ファイルからのすべてのシーケンス ポイントをマップするエントリを含める必要があります。  
  
 マップに存在しないエントリが補間されません。 次の例では、マップとその結果を示します。  
  
 マップ:  
  
- 以前のオフセットは 0、0 の新しいオフセット  
  
- 以前のオフセットが 5、10 の新しいオフセット  
  
- 以前のオフセットを 9、20 の新しいオフセット  
  
 結果:  
  
- 0、1、2、3、または 4 の以前のオフセットは、新しいオフセットは 0 にマップされます。  
  
- 5、6、7、または 8 の以前のオフセットは、10 の新しいオフセットにマップされます。  
  
- 9 以降の以前のオフセットは、20 の新しいオフセットにマップされます。  
  
- 0、1、2、3、4、5、6、7、8、または 9 の新しいオフセットは、以前のオフセット 0 にマップされます。  
  
- 10、11、12、13、14、15、16、17、18 または 19 の新しいオフセットは、以前のオフセット 5 にマップされます。  
  
- 20 以上の新しいオフセットは、以前のオフセット 9 にマップされます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl, CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
