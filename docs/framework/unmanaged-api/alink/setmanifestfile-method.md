---
title: SetManifestFile メソッド
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
ms.openlocfilehash: df97f4c37d8f335ce183685debd7c0933be910ed
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445564"
---
# <a name="setmanifestfile-method"></a>SetManifestFile メソッド
Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `pszFile`  
  
 The name of the manifest file whose contents are put into the Win32 resources blob.  
  
## <a name="return-value"></a>戻り値  
 Returns S_OK if the method succeeds.  
  
## <a name="remarks"></a>Remarks  
 Call this before asking for the Win32ResBlob. The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST. When called by using a parameter of NULL, any previously read manifest is cleared. This enables one to reset the state of the linker to that of initialization time.  
  
## <a name="requirements"></a>［要件］  
 Requires aLink.h  
  
## <a name="see-also"></a>関連項目

- [IALink3 インターフェイス](ialink3-interface.md)
- [ALink API](index.md)
- [IALink インターフェイス](ialink-interface.md)
- [Al.exe (アセンブリ リンカー)](../../tools/al-exe-assembly-linker.md)
