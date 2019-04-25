---
title: IMetaDataAssemblyImport::FindAssembliesByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b388dae0f109ff366f83c92de99b00b80bcc01a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905087"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName メソッド
指定したアセンブリの配列を取得します`szAssemblyName`パラメーター、参照を解決するための共通言語ランタイム (CLR) で採用されている標準の規則を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szAppBase`  
 [in]指定されたアセンブリを検索するためのルート ディレクトリ。 この値が設定されている場合`null`、`FindAssembliesByName`アセンブリはグローバル アセンブリ キャッシュでのみ検索します。  
  
 `szPrivateBin`  
 [in]セミコロンで区切られたサブディレクトリ (たとえば、「bin、bin2」)、アセンブリを検索するためのルート ディレクトリの下の一覧。 これらのディレクトリは、既定のルールをプローブで指定されているだけでなく検出されます。  
  
 `szAssemblyName`  
 [in]検索対象のアセンブリの名前。 クラスのリファレンス ページでこの文字列の形式が定義されている<xref:System.Reflection.AssemblyName>します。  
  
 `ppIUnk`  
 [in]型の配列[IUnknown](/cpp/atl/iunknown)配置される、`IMetadataAssemblyImport`インターフェイス ポインター。  
  
 `cMax`  
 [out]配置できるインターフェイス ポインターの最大数`ppIUnk`します。  
  
 `pcAssemblies`  
 [out]インターフェイス ポインターの数が返されます。 つまり、インターフェイス ポインターの数が実際に配置`ppIUnk`します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` 正常に返されます。|  
|`S_FALSE`|アセンブリがありません。|  
  
## <a name="remarks"></a>Remarks  
 特定のアセンブリ名、`FindAssembliesByName`メソッドは、アセンブリ参照を解決するための標準の規則に従って、アセンブリを検索します。 (詳細については、次を参照してください[ランタイムがアセンブリを検索する方法](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。)。`FindAssembliesByName`により、呼び出し元アセンブリの競合回避モジュール コンテキストのアプリケーションの基本とプライベートの検索パスなどのさまざまな側面を構成します。  
  
 `FindAssembliesByName`メソッドが、CLR アセンブリの解決ロジックを呼び出すために、プロセスで初期化する必要があります。 そのため、呼び出す必要がある[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (COINITEE_DEFAULT を渡す) 呼び出す前に`FindAssembliesByName`への呼び出しで次の[CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)します。  
  
 `FindAssembliesByName` 返します、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)で渡されるアセンブリの名前のアセンブリ マニフェストを含むファイルへのポインター。 (たとえば、バージョンが含まれていない場合)、指定したアセンブリ名が完全に指定されていない場合は、複数のアセンブリを返される可能性があります。  
  
 `FindAssembliesByName` コンパイル時に参照アセンブリを検索しようとするコンパイラで通常使用されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ランタイムがアセンブリを検索する方法](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
