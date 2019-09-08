---
title: GetTypeLibInfo 関数
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8ea7df9396e9199d04ad5609daa9d2b01761f36
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798893"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo 関数
指定したタイプライブラリに関する情報を返します。そのためには、その[Tlibattr](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr)構造体を調べます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szFile`  
 からタイプライブラリのファイル名。  
  
 `pTypeLibID`  
 入出力タイプライブラリの GUID。  
  
 `pTypeLibLCID`  
 入出力タイプライブラリのローカライズ ID。  
  
 `pTypeLibPlatform`  
 入出力タイプライブラリのターゲットオペレーティングシステムを識別する[SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind)フラグ。 共通値は SYS_WIN32 と SYS_WIN64 です。  
  
 `pTypeLibMajorVer`  
 入出力タイプライブラリのメジャーバージョン番号。 たとえば、バージョン*x.y*の場合、メジャーバージョン番号は*x*になります。  
  
 `pTypeLibMinorVer`  
 入出力タイプライブラリのマイナーバージョン番号。 たとえば、バージョン*x.y*の場合、マイナーバージョン番号は*y*になります。  
  
## <a name="remarks"></a>Remarks  
 この関数は、 [tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)によって呼び出されます。 `GetTypeLibInfo` このツールは、共通言語ランタイム (CLR) アセンブリ内の型を記述するタイプライブラリを生成します。  
  
 いずれか`HRESULT`のパラメーターが null の場合、関数は`E_POINTER`のを返します。 それ以外の場合は、 `S_OK`を返します。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Tlf .h  
  
 **ライブラリ**Tlf .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Tlbexp ヘルパー関数](index.md)
- [LoadTypeLibEx 関数](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
