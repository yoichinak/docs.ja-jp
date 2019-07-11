---
title: AssemblyOptions 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 324e30f6cbcaa1d1d81c7c03967dbb629d2cd6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742272"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions 列挙体
アセンブリ オプションを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>フィールド  
  
|フィールド|説明|  
|-----------|-----------------|  
|optAssemTitle|文字列 - アセンブリのタイトルを表します。|  
|optAssemDescription|文字列 - アセンブリの説明が含まれています。|  
|optAssemConfig|文字列 - アセンブリの構成が含まれています。|  
|optAssemOS|-エンコードされた文字列:"dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion"。|  
|optAssemProcessor|ULONG|  
|optAssemLocale|文字列 - アセンブリのロケールが含まれています。|  
|optAssemVersion|文字列 - としてエンコードされます。"Major.Minor.Build.Revision"。|  
|optAssemCompany|文字列 - 会社が含まれています。|  
|optAssemProduct|文字列 - 製品名が含まれています。|  
|optAssemProductVersion|文字列 (InformationalVersion とも呼ばれます)。|  
|optAssemCopyright|文字列 - 著作権情報が含まれています。|  
|optAssemTrademark|文字列 - 商標に関する情報が含まれています。|  
|optAssemKeyFile|String (ファイル名)。|  
|optAssemKeyName|文字列 (キー名)。|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (DelaySign とも呼ばれます)。|  
|optAssemFileVersion|文字列 -"Major.Minor.Build.Revision"--ProductVersion と同じようにエンコードします。|  
|optAssemSatelliteVer|文字列の"Major.Minor.Build.Revision"としてエンコードされます。|  
|optLastAssemOption|要素の数のカウンター。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** alink.h  
  
 **ライブラリ**: alink.dll  
  
## <a name="see-also"></a>関連項目

- [Al.exe (アセンブリ リンカー)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
