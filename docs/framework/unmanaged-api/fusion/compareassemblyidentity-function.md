---
title: CompareAssemblyIdentity 関数
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b52d3af38bd09ce5864c25d27e148dbd7f4639b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795446"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity 関数
2つのアセンブリ id を比較して、それらが等しいかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzAssemblyIdentity1`  
 から比較対象の最初のアセンブリのテキスト id。  
  
 `fUnified1`  
 からのユーザー指定の統一を示すブール型の`pwzAssemblyIdentity1`フラグ。  
  
 `pwzAssemblyIdentity2`  
 から比較対象の2番目のアセンブリのテキスト id。  
  
 `fUnified2`  
 からのユーザー指定の統一を示すブール型の`pwzAssemblyIdentity2`フラグ。  
  
 `pfEquivalent`  
 入出力2つのアセンブリが等しいかどうかを示すブール型のフラグ。  
  
 `pResult`  
 入出力比較に関する詳細情報を含む[AssemblyComparisonResult](assemblycomparisonresult-enumeration.md)列挙です。  
  
## <a name="return-value"></a>戻り値  
 `pfEquivalent`2つのアセンブリが等しいかどうかを示すブール値を返します。 `pResult`値の`AssemblyComparisonResult` 1 つを返し、の`pfEquivalent`値のより詳細な理由を指定します。  
  
## <a name="remarks"></a>Remarks  
 `CompareAssemblyIdentity`とが`pwzAssemblyIdentity1`等価`pwzAssemblyIdentity2`かどうかを確認します。 `pfEquivalent`は、次`true`の条件の1つ以上でに設定されます。  
  
- 2つのアセンブリ id は同等です。 厳密な名前が付けられたアセンブリの場合、等価性には、アセンブリ名、バージョン、公開キートークン、およびカルチャが同一である必要があります。 単純な名前付きアセンブリの場合、等価性にはアセンブリ名とカルチャの一致が必要です。  
  
- どちらのアセンブリ id も、.NET Framework で実行されるアセンブリを参照します。 この条件は`true` 、アセンブリのバージョン番号が一致しない場合でもを返します。  
  
- 2つのアセンブリはマネージアセンブリでは`fUnified1`あり`fUnified2`ませんが`true`、またはがに設定されています。  
  
 フラグ`fUnified`は、厳密な名前が付けられたアセンブリのバージョン番号までのすべてのバージョン番号が、厳密に名前が付けられたアセンブリと同等であると見なされることを示します。 たとえば、の`pwzAssemblyIndentity1`値が "MyAssembly, version = 3.0.0.0, culture = ニュートラル, publicKeyToken =..." で、の値が`true`の`fUnified1`場合、バージョン0.0.0.0 から3.0.0.0 のすべてのバージョンの MyAssembly がである必要があることを示します。同等として扱われます。 このような`pwzAssemblyIndentity2`場合、 `pfEquivalent`がと`pwzAssemblyIndentity1`同じアセンブリを参照している場合は、バージョン番号が低い点がに`true`設定されます。 が`pwzAssemblyIdentity2`より上位のバージョン番号を参照`pfEquivalent`している`true`場合、の`fUnified2`値が`true`である場合にのみがに設定されます。  
  
 パラメーター `pResult`には、2つのアセンブリが同等であるかどうかについての特定の情報が含まれます。 詳細については、「 [AssemblyComparisonResult 列挙型](assemblycomparisonresult-enumeration.md)」を参照してください。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion グローバル静的関数](fusion-global-static-functions.md)
- [AssemblyComparisonResult 列挙型](assemblycomparisonresult-enumeration.md)
