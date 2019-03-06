---
title: ResolveTypeLib メソッド
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b87460b9e525f2cf91b8f177c06286b5bbb3c52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486122"
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib メソッド
完全修飾パスを返すことによって、タイプ ライブラリの簡易名を解決します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a>パラメーター  
 `bstrSimpleName`  
 [in]A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr)タイプ ライブラリの簡易名を格納しています。  
  
 `tlbid`  
 [in]レジストリでタイプ ライブラリに割り当てられた GUID です。  
  
 `lcid`  
 [in]タイプ ライブラリのローカリゼーション ID。  
  
 `wMajorVersion`  
 [in]タイプ ライブラリのメジャー バージョン番号。 たとえば、バージョン*x.y*、メジャー バージョン番号は*x*します。  
  
 `wMinorVersion`  
 [in]タイプ ライブラリのマイナー バージョン番号。 たとえば、バージョン*x.y*、マイナー バージョン番号は*y*します。  
  
 `syskind`  
 [in]A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind)オペレーティング環境を識別するフラグ。 一般的な値は SYS_WIN32 および SYS_WIN64 です。  
  
 `pbstrResolvedTlbName`  
 [out]ポインターを[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr)でという名前のタイプ ライブラリの完全なパスを格納している、`bstrSimpleName`パラメーター。  
  
## <a name="remarks"></a>Remarks  
 `ResolveTypeLib`メソッドを呼び出して、 [LoadTypeLibWithResolver 関数](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)中に[Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)処理します。  
  
 このインターフェイスのカスタム実装を返す必要があります、 [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr)でという名前のタイプ ライブラリの完全なパスを格納している、`bstrSimpleName`パラメーター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** TlbRef.idl、TlbRef.h  
  
 **ライブラリ:** TlbRef.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [Tlbexp ヘルパー関数](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
