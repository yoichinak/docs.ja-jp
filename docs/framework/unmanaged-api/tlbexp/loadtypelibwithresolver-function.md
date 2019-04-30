---
title: LoadTypeLibWithResolver 関数
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c14080e3ac128a6a7fbb48586f59d8a5ea4105f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049337"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver 関数
タイプ ライブラリを読み込み、指定された使用[ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)任意の内部で参照されるタイプ ライブラリを解決します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szFile`  
 [in]タイプ ライブラリのファイル パス。  
  
 `regkind`  
 [in]A [REGKIND 列挙](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind)タイプ ライブラリを登録する方法を制御するフラグ。 指定できる値は次のとおりです。  
  
- `REGKIND_DEFAULT`:既定の登録の動作を使用します。  
  
- `REGKIND_REGISTER`:このタイプ ライブラリを登録します。  
  
- `REGKIND_NONE`:このタイプ ライブラリを登録できません。  
  
 `pTlbResolver`  
 [in]実装へのポインター、 [ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)します。  
  
 `pptlib`  
 [out]読み込まれているタイプ ライブラリへの参照。  
  
## <a name="return-value"></a>戻り値  
 次の表に記載した HRESULT 値の 1 つ。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|メモリが不足しています。|  
|`E_POINTER`|1 つ以上のポインターが無効です。|  
|`E_INVALIDARG`|1 つ以上の引数が無効です。|  
|`TYPE_E_IOERROR`|関数は、ファイルに書き込めませんでした。|  
|`TYPE_E_REGISTRYACCESS`|システムの登録情報データベースを開くことができませんでした。|  
|`TYPE_E_INVALIDSTATE`|タイプ ライブラリを開くことができませんでした。|  
|`TYPE_E_CANTLOADLIBRARY`|タイプ ライブラリまたは DLL を読み込むことができませんでした。|  
  
## <a name="remarks"></a>Remarks  
 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)呼び出し、`LoadTypeLibWithResolver`アセンブリをタイプ ライブラリへの変換処理中に機能します。  
  
 この関数は、レジストリに最小限のアクセス権を持つ指定したタイプ ライブラリを読み込みます。 関数は、内部で参照されるタイプ ライブラリ、それぞれが読み込まれ、親のタイプ ライブラリに追加する必要がありますのタイプ ライブラリを調べます。  
  
 参照されるタイプ ライブラリは、読み込まれる前に、ファイルの完全パスにファイルのパスを参照を解決する必要があります。 これによって実現されます、 [ResolveTypeLib メソッド](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md)によって提供される、 [ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)に渡される、`pTlbResolver`パラメーター。  
  
 参照されるタイプ ライブラリの完全ファイル パスがわかっている場合、`LoadTypeLibWithResolver`関数が読み込みを結合されたマスターのタイプ ライブラリを作成する、親のタイプ ライブラリに参照されるタイプ ライブラリを追加します。  
  
 関数は解決し、すべての内部で参照されるタイプ ライブラリを読み込み後で解決されたマスター タイプ ライブラリへの参照を返します、`pptlib`パラメーター。  
  
 `LoadTypeLibWithResolver`関数一般に、 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)、独自の内部を供給する[ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)での実装、 `pTlbResolver`パラメーター。  
  
 呼び出す場合`LoadTypeLibWithResolver`を直接指定する必要あります独自[ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)実装します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** TlbRef.h  
  
 **ライブラリ:** TlbRef.lib  
  
 **.NET framework のバージョン:** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>関連項目

- [Tlbexp ヘルパー関数](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx 関数](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
