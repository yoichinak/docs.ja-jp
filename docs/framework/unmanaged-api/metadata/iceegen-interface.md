---
title: ICeeGen インターフェイス
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
ms.openlocfilehash: ae3c372951de00b097d0a8437039a3a85bf3aabf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426154"
---
# <a name="iceegen-interface"></a>ICeeGen インターフェイス
動的なコード コンパイルのためのメソッドを提供します。  
  
 This interface is obsolete and should not be used.  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AddSectionReloc メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|互換性のために残されています。 Adds a .reloc instruction to the code base.|  
|[AllocateMethodBuffer メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|互換性のために残されています。 Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.|  
|[ComputePointer メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|互換性のために残されています。 Determines the buffer for the specified code section.|  
|[EmitString メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|互換性のために残されています。 Emits the specified string into the code base.|  
|[GenerateCeeFile メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|互換性のために残されています。 Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.|  
|[GenerateCeeMemoryImage メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|互換性のために残されています。 Generates an image in memory for the code base.|  
|[GetIlSection メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|互換性のために残されています。 Gets the section of the intermediate language code base referenced by the specified handle.|  
|[GetIMapTokenIface メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|互換性のために残されています。 Gets the interface referenced by the specified token.|  
|[GetMethodBuffer メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|互換性のために残されています。 Gets a buffer of the appropriate size for the method at the specified relative virtual address.|  
|[GetSectionBlock メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|互換性のために残されています。 Gets a section block of the code base.|  
|[GetSectionCreate メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|互換性のために残されています。 Generates and gets a code section using the specified name and flag values.|  
|[GetSectionDataLen メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|互換性のために残されています。 Gets the length of the specified section.|  
|[GetString メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|互換性のために残されています。 Gets the string stored at the specified relative virtual address.|  
|[GetStringSection メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|互換性のために残されています。 Gets a string representation of the code section referenced by the specified handle.|  
|[TruncateSection メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|互換性のために残されています。 Truncates the specified code section by the specified length.|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
