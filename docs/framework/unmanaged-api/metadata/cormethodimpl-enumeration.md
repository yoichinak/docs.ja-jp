---
title: CorMethodImpl 列挙型
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2138dd32cf39db7b7c8989ba5827178d1a1e46c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045566"
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl 列挙型
メソッド実装の機能を記述する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`miCodeTypeMask`|コードの種類を記述するフラグ。|  
|`miIL`|メソッドの実装が Microsoft intermediate language (MSIL) であることを指定します。|  
|`miNative`|メソッド実装がネイティブであることを指定します。|  
|`miOPTIL`|メソッドの実装が OPTIL であることを指定します。|  
|`miRuntime`|メソッドの実装が、共通言語ランタイムによって提供されることを指定します。|  
|`miManagedMask`|コードがマネージかアンマネージかどうかを示すフラグです。|  
|`miUnmanaged`|メソッドの実装が管理されていないことを指定します。|  
|`miManaged`|メソッドの実装が管理されていることを指定します。|  
|`miForwardRef`|メソッドが定義されていることを指定します。 このフラグは、マージのシナリオで主に使用されます。|  
|`miPreserveSig`|メソッドのシグネチャは、その HRESULT 変換では変形ことはできませんを指定します。|  
|`miInternalCall`|共通言語ランタイムでは、内部使用のため予約されています。|  
|`miSynchronized`|メソッドがその内部から、シングル スレッドであるを指定します。|  
|`miNoInlining`|メソッドがインライン化できないことを指定します。|  
|`miAggressiveInlining`|メソッドがインライン化できません可能な場合を指定します。|  
|`miNoOptimization`|メソッドを最適化されていないことを指定します。|  
|`miMaxMethodImplVal`|最大有効値、`CorMethodImpl`します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
