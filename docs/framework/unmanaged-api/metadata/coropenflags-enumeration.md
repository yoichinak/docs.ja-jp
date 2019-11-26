---
title: CorOpenFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
ms.openlocfilehash: ad582fc2fd1bd1d2fc9d5a0d483fdb3a51309a10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436507"
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags 列挙型
マニフェスト ファイルを開くときにメタデータの動作を制御するフラグ値を含めます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ofRead`|ファイルが読み取り専用で開かれることを示します。|  
|`ofWrite`|ファイルが書き込み用に開かれることを示します。<br /><br /> .winmd ファイルを開くときに `ofWrite` フラグを使用する場合は、`ofNoTransform` フラグも渡す必要があります。|  
|`ofReadWriteMask`|読み取りおよび書き込み用のマスク。|  
|`ofCopyMemory`|ファイルがメモリ内に読み込まれることを示します。 メタデータは自身のコピーを保持する必要があります。|  
|`ofCacheImage`|互換性のために残されています。 このフラグは無視されます。|  
|`ofManifestMetadata`|互換性のために残されています。 このフラグは無視されます。|  
|`ofReadOnly`|Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.|  
|`ofTakeOwnership`|Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.|  
|`ofNoTypeLib`|互換性のために残されています。 このフラグは無視されます。|  
|`ofNoTransform`|.winmd ファイルの自動変換を無効にする必要があることを示します。 つまり、Windows Runtime タイプから .NET Framework タイプへの投射は無効になります。 For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).|  
|`ofReserved1`|内部使用のために予約されています。|  
|`ofReserved2`|内部使用のために予約されています。|  
|`ofReserved`|内部使用のために予約されています。|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
