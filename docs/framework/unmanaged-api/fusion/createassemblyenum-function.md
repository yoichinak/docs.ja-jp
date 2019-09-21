---
title: CreateAssemblyEnum 関数
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795380"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum 関数
指定された[IAssemblyName](iassemblyname-interface.md)を持つアセンブリ内のオブジェクトを列挙できる[iassemblyenum](iassemblyenum-interface.md)インスタンスへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>パラメーター  
 `pEnum`  
 入出力要求さ`IAssemblyEnum`れたポインターを格納しているメモリ位置へのポインター。  
  
 `pUnkReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `pUnkReserved`null 参照である必要があります。  
  
 `pName`  
 から要求されたアセンブリの。`IAssemblyName` この名前は、列挙をフィルター処理するために使用されます。 グローバルアセンブリキャッシュ内のすべてのアセンブリを列挙するには null を指定できます。  
  
 `dwFlags`  
 から列挙子の動作を変更するためのフラグ。 このパラメーターには、 [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md)列挙体とのビットが1つだけ含まれます。  
  
 `pvReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `pvReserved`null 参照である必要があります。  
  
## <a name="remarks"></a>Remarks  
 パラメーター `dwFlags`には、 `ASM_CACHE_FLAGS`列挙体のビットが1つだけ含まれます。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IAssemblyEnum インターフェイス](iassemblyenum-interface.md)
- [IAssemblyName インターフェイス](iassemblyname-interface.md)
- [Fusion グローバル静的関数](fusion-global-static-functions.md)
