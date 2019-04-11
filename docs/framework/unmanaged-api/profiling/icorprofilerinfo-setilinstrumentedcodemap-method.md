---
title: ICorProfilerInfo::SetILInstrumentedCodeMap メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a574a04e5746a8b2c9c32160e82aa503b392729
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154194"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap メソッド
指定された Microsoft intermediate language (MSIL) のマップ エントリを使用して、指定された関数のコード マップを設定します。  
  
> [!NOTE]
>  呼び出す .NET Framework version 2.0 で`SetILInstrumentedCodeMap`で、`FunctionID`ジェネリック関数の特定のアプリケーション ドメインで表すには、アプリケーション ドメインでは、その関数のすべてのインスタンスに影響します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]コード マップを設定する対象の関数の ID。  
  
 `fStartJit`  
 [in]示すブール値かどうかを呼び出し、`SetILInstrumentedCodeMap`メソッドは、特定の 1 つ目`FunctionID`します。 設定`fStartJit`に`true`最初の呼び出しで`SetILInstrumentedCodeMap`の指定された`FunctionID`、および`false`以降。  
  
 `cILMapEntries`  
 [in]要素の数、`cILMapEntries`配列。  
  
 `rgILMapEntries`  
 [in]COR_IL_MAP 構造体の MSIL オフセットを指定の配列。  
  
## <a name="remarks"></a>Remarks  
 プロファイラーは、(たとえば、指定されたソース行に達したときに通知する場合など) には、そのメソッドをインストルメント化するために多くの場合、メソッドのソース コード内のステートメントを挿入します。 `SetILInstrumentedCodeMap` 元の MSIL 命令を新しい場所にマップするプロファイラーを有効にします。 プロファイラーを使用できる、 [icorprofilerinfo::getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)特定のネイティブ オフセットの元の MSIL オフセットを取得します。  
  
 デバッガーには、古い各オフセットが、変更されていない元の MSIL コード内のオフセット、MSIL を指すことと、新しい各オフセットがインストルメント化された新しいコード内の MSIL オフセットを指すことが前提としています。 マップは、昇順で並べ替え 必要があります。 適切に機能するステップの場合これらのガイドラインに従います。  
  
-   インストルメント化された MSIL コードの順序を変更しません。  
  
-   元の MSIL コードを削除しないでください。  
  
-   マップでは、プログラム データベース (PDB) ファイルからのすべてのシーケンス ポイントのエントリを含めます。 マップに存在しないエントリが補間されません。 そのため、次のマップを考えてみます。  
  
     (新しい 0、0)  
  
     (新しい 5、10)  
  
     (新しい 9、20)  
  
    -   0、1、2、3、または 4 の以前のオフセットは、新しいオフセット 0 にマップされます。  
  
    -   5、6、7、または 8 の以前のオフセットは、10 の新しいオフセットにマップされます。  
  
    -   9 以降の以前のオフセットは、20 の新しいオフセットにマップされます。  
  
    -   0、1、2、3、4、5、6、7、8、または 9 の新しいオフセットは、以前のオフセット 0 にマップされます。  
  
    -   10、11、12、13、14、15、16、17、18 または 19 の新しいオフセットは、以前のオフセット 5 にマップされます。  
  
    -   20 以上の新しいオフセットは、以前のオフセット 9 にマップされます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
