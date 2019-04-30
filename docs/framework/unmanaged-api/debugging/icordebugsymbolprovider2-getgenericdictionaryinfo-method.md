---
title: ICorDebugSymbolProvider2::GetGenericDictionaryInfo メソッド
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f171af8dbfa4e812711e95e5587b314753cd9350
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944650"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>ICorDebugSymbolProvider2::GetGenericDictionaryInfo メソッド
汎用のディクショナリ マップを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppMemoryBuffer`  
 [out]アドレスへのポインター、 [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)汎用のディクショナリ マップを含むオブジェクト。 詳細については、次の「解説」を参照してください。  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
 このマップは最上位レベルの 2 つのセクションで構成されています。  
  
- A[ディレクトリ](#Directory)このマップに含まれるすべてのディクショナリの相対仮想アドレス (RVA) を格納しています。  
  
- バイト揃え[ヒープ](#Heap)オブジェクトのインスタンス化情報を格納します。 最後のディレクトリ エントリの直後から開始します。  
  
<a name="Directory"></a>   
## <a name="the-directory"></a>ディレクトリ  
 ディレクトリ内の各エントリは、ヒープ内のオフセットを参照します。つまり、これは、ヒープの開始位置を基準としたオフセットです。 個々のエントリの値が一意とは限りません。このため、複数のディクショナリ エントリがヒープ内の同一オフセットを指すことがあります。  
  
 汎用のディクショナリ マップのディレクトリ部分の構造は次のとおりです。  
  
- 最初の 4 バイトには、ディクショナリのエントリ数 (ディクショナリ内の相対仮想アドレスの数) が格納されています。 この値として参照*N*します。上位ビットが設定されている場合、エントリは相対仮想アドレスに基づいて昇順で並べ替えられます。  
  
- *N*ディレクトリ エントリに従ってください。 各エントリは 8 バイトであり、次の 2 つの 4 バイト セグメントからなります。  
  
    - 0 ~ 3 のバイト数:RVA です。ディクショナリの相対仮想アドレス。  
  
    - バイト 4 ~ 7:オフセット。ヒープの先頭からの相対オフセット。  
  
<a name="Heap"></a>   
## <a name="the-heap"></a>ヒープ  
 ヒープのサイズは、ストリーム リーダーにより、ディレクトリ サイズ + 4 の値からストリームの長さを差し引くことで算出されます。 つまり、次のようになります。  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 ディレクトリのサイズが `N * 8` であるとします。  
  
 ヒープの各インスタンス化情報項目の形式は次のとおりです。  
  
- このインスタンス化情報項目のバイト単位の長さ。圧縮 ECMA メタデータ形式です。 値では、この長さ情報が除外されます。  
  
- ジェネリックなインスタンス化の種類の数または*T*、圧縮 ECMA メタデータ形式にします。  
  
- *T* ECMA 型シグネチャ形式で表されるそれぞれの種類。  
  
 各ヒープ要素の長さを含めることで、ヒープに影響を与えずに、ディレクトリ セクションの単純な並べ替えを実行できるようになります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugSymbolProvider2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
