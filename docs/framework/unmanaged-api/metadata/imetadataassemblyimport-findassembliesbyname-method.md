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
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177801"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName メソッド
共通言語ランタイム (CLR) で参照`szAssemblyName`を解決するために使用される標準規則を使用して、指定したパラメーターを持つアセンブリの配列を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [in]指定したアセンブリを検索するルート ディレクトリ。 この値を に`null``FindAssembliesByName`設定すると、アセンブリのグローバル アセンブリ キャッシュ内でのみ検索されます。  
  
 `szPrivateBin`  
 [in]アセンブリを検索するルート ディレクトリの下にあるセミコロン区切りのサブディレクトリ ("bin;bin2"など) のリスト。 これらのディレクトリは、デフォルトのプローブ規則で指定されたディレクトリに加えてプローブされます。  
  
 `szAssemblyName`  
 [in]検索するアセンブリの名前。 この文字列の形式は、 のクラスリファレンス ページで<xref:System.Reflection.AssemblyName>定義されます。  
  
 `ppIUnk`  
 [in]インターフェイス ポインターを配置する[IUnknown](/cpp/atl/iunknown)型`IMetadataAssemblyImport`の配列。  
  
 `cMax`  
 [アウト]に配置できるインターフェイス ポインタの最大数`ppIUnk`。  
  
 `pcAssemblies`  
 [アウト]返されるインターフェイス ポインターの数。 つまり、実際に にに配置されるインターフェイス ポインター`ppIUnk`の数です。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`正常に返されました。|  
|`S_FALSE`|アセンブリはありません。|  
  
## <a name="remarks"></a>解説  
 アセンブリ名を指定すると`FindAssembliesByName`、メソッドは、アセンブリ参照を解決するための標準規則に従ってアセンブリを検索します。 (詳細については、「[ランタイムがアセンブリを検索する方法](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」を参照してください)。`FindAssembliesByName`呼び出し元は、アプリケーション ベースやプライベート検索パスなど、アセンブリ リゾルバー コンテキストのさまざまな側面を構成できます。  
  
 この`FindAssembliesByName`メソッドでは、アセンブリ解決ロジックを呼び出すために、プロセスで CLR を初期化する必要があります。 したがって、呼び出す前に[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (COINITEE_DEFAULT渡す) を呼び出`FindAssembliesByName`してから[、CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)の呼び出しを実行する必要があります。  
  
 `FindAssembliesByName`渡されたアセンブリ名のアセンブリ マニフェストを含むファイルへの[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)ポインターを返します。 指定されたアセンブリ名が完全に指定されていない場合 (たとえば、バージョンが含まれていない場合)、複数のアセンブリが返される可能性があります。  
  
 `FindAssembliesByName`は、コンパイル時に参照アセンブリを検索しようとするコンパイラで一般的に使用されます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ランタイムがアセンブリを検索する方法](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
