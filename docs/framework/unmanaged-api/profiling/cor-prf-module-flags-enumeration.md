---
title: COR_PRF_MODULE_FLAGS 列挙体
ms.date: 03/30/2017
api_name:
- COR_PRF_MODULE_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MODULE_FLAGS
helpviewer_keywords:
- COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98fee786a7acb87598baabed62067b599907bede
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599144"
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS 列挙体
モジュールのプロパティを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum  
{  
    COR_PRF_MODULE_DISK             = 0x00000001,  
    COR_PRF_MODULE_NGEN             = 0x00000002,  
    COR_PRF_MODULE_DYNAMIC          = 0x00000004,  
    COR_PRF_MODULE_COLLECTIBLE      = 0x00000008,  
    COR_PRF_MODULE_RESOURCE         = 0x00000010,  
    COR_PRF_MODULE_FLAT_LAYOUT      = 0x00000020,  
    COR_PRF_MODULE_WINDOWS_RUNTIME  = 0x00000040  
}   COR_PRF_MODULE_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|モジュールは、ディスクから読み込まれました。|  
|COR_PRF_MODULE_NGEN|モジュールは、ネイティブ イメージ ジェネレーター (Ngen.exe) によって生成されました。|  
|COR_PRF_MODULE_DYNAMIC|メソッドによって作成されたモジュール、<xref:System.Reflection.Emit?displayProperty=nameWithType>名前空間。|  
|COR_PRF_MODULE_COLLECTIBLE|モジュールの有効期間は、ガベージ コレクターによって管理されます。|  
|COR_PRF_MODULE_RESOURCE|モジュールは、メタデータが含まれていないし、リソースとしてにのみ使用されます。 このビットのマネージ バージョンは、<xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType>メソッド。|  
|COR_PRF_MODULE_FLAT_LAYOUT|メモリ内のモジュールのレイアウトはフラットでマップされていません。 場合、モジュールがこのビットが設定、プロファイラーで読み取るポータブル実行可能 (PE) ファイル ヘッダーから直接情報がヘッダー内の相対仮想アドレス (Rva) を解釈するときに注意する必要があります。|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Windows ランタイムのコンテンツの種類のフラグは、このモジュールのアセンブリのメタデータで設定されます。 これは、すべての Windows メタデータ (.winmd) モジュールの場合です。|  
  
## <a name="remarks"></a>Remarks  
 プロファイラーに返されるビットは COR_PRF_MODULE_FLAGS から、`pdwModuleFlags`出力パラメーター、 [icorprofilerinfo 3::getmoduleinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)メソッド。 2 つ以上のフラグのいくつかの組み合わせが可能であればがすべての組み合わせが可能です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
