---
title: ISymUnmanagedWriter::GetDebugInfo メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce74b043db67fa1086724dd76001935f9c1c0498
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470949"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo メソッド
コンパイラがポータブル実行可能 (PE) ファイル ヘッダーのデバッグ ディレクトリのエントリを書き込むために必要な情報を返します。 シンボル ライターを除くのすべてのフィールドは`TimeDateStamp`と`PointerToRawData`します。 (コンパイラは、これら 2 つのフィールドを適切に設定を行います)。  
  
 このメソッドを呼び出す、PE ファイルまでデータ blob の出力、設定する必要があります、コンパイラ、 `PointerToRawData` 、出力されたデータをポイントして、IMAGE_DEBUG_DIRECTORY を PE ファイルに書き込む IMAGE_DEBUG_DIRECTORY フィールド。 コンパイラを設定する必要がありますも、`TimeDateStamp`フィールドと等しい、 `TimeDateStamp` PE ファイルが生成されるのです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pIDD`  
 [入力、出力]シンボルのライターが入力する、IMAGE_DEBUG_DIRECTORY へのポインター。  
  
 `cData`  
 [in]A`DWORD`デバッグ データのサイズを格納しています。  
  
 `pcData`  
 [out]ポインターを`DWORD`デバッグ データの格納に必要なバッファーのサイズを受け取る。  
  
 `data`  
 [out]シンボル ストアのデバッグ データを保持するために十分な大きさであるバッファーへのポインター。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目
- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
