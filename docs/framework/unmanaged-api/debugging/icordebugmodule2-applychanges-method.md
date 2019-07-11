---
title: ICorDebugModule2::ApplyChanges メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 860b87b09ee487f893a1bba2aaa34292c50ffcb7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764342"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges メソッド
実行中のプロセスにメタデータの変更と Microsoft intermediate language (MSIL) コードの変更を適用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cbMetadata`  
 [in]デルタのメタデータのバイト単位のサイズ。  
  
 `pbMetadata`  
 [in]デルタのメタデータを格納するバッファー。 バッファーのアドレスから返される、 [imetadataemit 2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)メソッド。  
  
 MSIL コードの先頭からの相対メタデータ内の相対仮想アドレス (Rva) があります。  
  
 `cbIL`  
 [in]デルタの MSIL コードのバイト単位のサイズ。  
  
 `pbIL`  
 [in]更新された MSIL コードを格納するバッファー。  
  
## <a name="remarks"></a>Remarks  
 `pbMetadata`パラメーターは、特別なデルタ メタデータ形式では (によって出力として[imetadataemit 2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md))。 `pbMetadata` ベースとして前のメタデータを受け取り、そのベースに適用する個々 の変更について説明します。  
  
 これに対し、 `pbIL[`] パラメーターが新しい、更新されたメソッドの MSIL を含むし、そのメソッドの以前の MSIL を完全に置き換えるものでは  
  
 デバッガーのメモリ内で、デルタ MSIL とメタデータが作成されると、デバッガーが呼び出す`ApplyChanges`共通言語ランタイム (CLR) に変更を送信します。 ランタイムは、そのメタデータ テーブルを更新、新しい MSIL をプロセスに配置し、新しい MSIL のジャストイン タイム (JIT) コンパイルを設定します。 変更が適用されている場合、デバッガーを呼び出す必要があります[imetadataemit 2::resetenclog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) [次へ] の編集セッションを準備します。 デバッガーは、プロセスを続行することがあります。  
  
 デバッガーを呼び出すたびに`ApplyChanges`デルタのメタデータを含むモジュールの場合に呼び出す必要もあります[imetadataemit::applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)コピーを除き、そのモジュールのメタデータのコピーのすべてに同じデルタ メタデータを持つ変更内容を出力するために使用します。 場合は、メタデータのコピーは、非同期の何らかの方法でになります。 実際のメタデータとデバッガー常にそのコピーを破棄して新しいコピーを取得します。  
  
 場合、`ApplyChanges`メソッドが失敗した場合は、デバッグ セッションが無効の状態と、再起動する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
