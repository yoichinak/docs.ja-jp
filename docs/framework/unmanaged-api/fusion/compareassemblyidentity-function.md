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
ms.openlocfilehash: 652000367c19572f73296c704047830ce1c74574
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914525"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity 関数
2 つのアセンブリ id と同じかどうかを比較します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]比較では、最初のアセンブリのテキスト形式の id。  
  
 `fUnified1`  
 [in]ユーザー指定の統一を示すブール フラグ`pwzAssemblyIdentity1`します。  
  
 `pwzAssemblyIdentity2`  
 [in]比較では、2 番目のアセンブリのテキスト形式の id。  
  
 `fUnified2`  
 [in]ユーザー指定の統一を示すブール フラグ`pwzAssemblyIdentity2`します。  
  
 `pfEquivalent`  
 [out]2 つのアセンブリが等しいかどうかを示すブール フラグです。  
  
 `pResult`  
 [out][AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)比較に関する詳細情報を含む列挙です。  
  
## <a name="return-value"></a>戻り値  
 `pfEquivalent` 2 つのアセンブリが等しいかどうかを示すブール値を返します。 `pResult` いずれかを返します、`AssemblyComparisonResult`の値の詳細な理由を指定する値、`pfEquivalent`します。  
  
## <a name="remarks"></a>Remarks  
 `CompareAssemblyIdentity` チェックするかどうか`pwzAssemblyIdentity1`と`pwzAssemblyIdentity2`は同等です。 `pfEquivalent` 設定されている`true`次の条件の 1 つ以上。  
  
-   2 つのアセンブリ id は同等です。 アセンブリ名、バージョン、公開キー トークン、およびカルチャと同じですが、厳密な名前付きアセンブリのと同等のグループが必要です。 単純な名前のアセンブリと同等のグループにはアセンブリ名、およびカルチャに一致する必要があります。  
  
-   両方のアセンブリ id は、.NET Framework で実行されるアセンブリを参照してください。 この条件の戻り値`true`場合でも、アセンブリのバージョン番号が一致しません。  
  
-   2 つのアセンブリは、マネージ アセンブリではありませんが、`fUnified1`または`fUnified2`に設定された`true`します。  
  
 `fUnified`フラグは、厳密な名前付きアセンブリのバージョン番号までのすべてのバージョン番号同等と見なされる厳密な名前付きアセンブリにことを示します。 たとえば場合の値`pwzAssemblyIndentity1`が"MyAssembly, バージョン 3.0.0.0, culture = = neutral, publicKeyToken =..."の値と`fUnified1`は`true`、MyAssembly 0.0.0.0 に 3.0.0.0 のバージョンからのすべてのバージョンがあることを示します同等として扱われます。 このような場合は場合、`pwzAssemblyIndentity2`と同じアセンブリを指す`pwzAssemblyIndentity1`、低いバージョン番号があることを除いて、`pfEquivalent`に設定されている`true`します。 場合`pwzAssemblyIdentity2`上位のバージョン番号を指す`pfEquivalent`に設定されている`true`場合にのみの値`fUnified2`は`true`します。  
  
 `pResult`パラメーターには、なぜ 2 つのアセンブリは同等または同等ではないと見なされますに関する特定の情報が含まれています。 詳細については、次を参照してください。 [AssemblyComparisonResult 列挙型](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [AssemblyComparisonResult 列挙型](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
