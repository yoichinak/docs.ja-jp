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
ms.openlocfilehash: b78789344050fd5e1cb0ee3492bf330fbf92bc88
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798937"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver 関数
タイプライブラリを読み込み、指定された[ITypeLibResolver インターフェイス](itypelibresolver-interface.md)を使用して、内部で参照されているタイプライブラリを解決します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szFile`  
 からタイプライブラリのファイルパス。  
  
 `regkind`  
 からタイプライブラリの登録方法を制御する[Regkind 列挙](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind)フラグ。 指定できる値は次のとおりです。  
  
- `REGKIND_DEFAULT`:既定の登録動作を使用します。  
  
- `REGKIND_REGISTER`:このタイプライブラリを登録します。  
  
- `REGKIND_NONE` :このタイプライブラリを登録しないでください。  
  
 `pTlbResolver`  
 から[ITypeLibResolver インターフェイス](itypelibresolver-interface.md)の実装へのポインター。  
  
 `pptlib`  
 入出力読み込まれているタイプライブラリへの参照。  
  
## <a name="return-value"></a>戻り値  
 次の表に示す HRESULT 値の1つ。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|メモリ不足。|  
|`E_POINTER`|1つ以上のポインターが無効です。|  
|`E_INVALIDARG`|1つ以上の引数が無効です。|  
|`TYPE_E_IOERROR`|関数はファイルに書き込めませんでした。|  
|`TYPE_E_REGISTRYACCESS`|システム登録データベースを開けませんでした。|  
|`TYPE_E_INVALIDSTATE`|タイプライブラリを開けませんでした。|  
|`TYPE_E_CANTLOADLIBRARY`|タイプライブラリまたは DLL を読み込めませんでした。|  
  
## <a name="remarks"></a>Remarks  
 [Tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)は、アセンブリからタイプ`LoadTypeLibWithResolver`ライブラリへの変換プロセス中に関数を呼び出します。  
  
 この関数は、レジストリへの最小限のアクセスで、指定されたタイプライブラリを読み込みます。 次に、関数は、内部的に参照されるタイプライブラリのタイプライブラリを調べます。このタイプライブラリはそれぞれ、親タイプライブラリに読み込まれ、追加される必要があります。  
  
 参照されるタイプライブラリを読み込む前に、その参照ファイルのパスを完全なファイルパスに解決する必要があります。 これは、 `pTlbResolver`パラメーターで渡される[ITypeLibResolver インターフェイス](itypelibresolver-interface.md)によって提供される[resolvetypelib メソッド](resolvetypelib-method.md)を使用して実現されます。  
  
 参照されているタイプライブラリの完全なファイルパスがわかっ`LoadTypeLibWithResolver`ている場合、この関数は参照されているタイプライブラリを読み込んで親タイプライブラリに追加し、結合されたマスタータイプライブラリを作成します。  
  
 関数は、内部的に参照されるすべてのタイプライブラリを解決して読み込み、 `pptlib`パラメーター内のマスター解決済みタイプライブラリへの参照を返します。  
  
 この関数は、通常、 [tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)によって呼び出されます。これは、 `pTlbResolver`パラメーターに独自の内部[ITypeLibResolver インターフェイス](itypelibresolver-interface.md)実装を提供します。 `LoadTypeLibWithResolver`  
  
 を直接呼び出す`LoadTypeLibWithResolver`場合は、独自の[ITypeLibResolver インターフェイス](itypelibresolver-interface.md)実装を指定する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Tlf .h  
  
 **ライブラリ**Tlf .lib  
  
 **.NET Framework のバージョン:** 3.5、3.0、2.0  
  
## <a name="see-also"></a>関連項目

- [Tlbexp ヘルパー関数](index.md)
- [LoadTypeLibEx 関数](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
