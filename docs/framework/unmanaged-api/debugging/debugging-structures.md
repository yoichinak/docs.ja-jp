---
title: デバッグ構造体
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50db519410b9513725c3dc10637421ba8bb37ec
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965229"
---
# <a name="debugging-structures"></a>デバッグ構造体

このセクションでは、デバッグ API が使用するアンマネージ構造体について説明します。

## <a name="in-this-section"></a>このセクションの内容
 [CLRDATA_ADDRESS_RANGE 構造](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md)アドレスの範囲を定義します。

 [CLRDATA_IL_ADDRESS_MAP 構造](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md)アドレスへのマッピングから、IL を定義します。

 [CLR_DEBUGGING_VERSION 構造体](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)デバッグのための共通言語ランタイム (CLR) の製品バージョンを定義します。

 [CodeChunkInfo 構造体](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)メモリ内のコードの 1 つのチャンクを表します。

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md)スレッドのフレームで現在アクティブな関数についての情報が含まれています。

 [COR_ARRAY_LAYOUT 構造体](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)メモリ内配列オブジェクトのレイアウトに関する情報を提供します。

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Microsoft intermediate language (MSIL) にマップするために使用されるオフセットがネイティブ コードにコードが含まれます。

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md)コードの範囲に関するオフセット情報が含まれています。

 [COR_FIELD 構造体](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)オブジェクトのフィールドに関する情報を提供します。

 [COR_GC_REFERENCE 構造体](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)ガベージ コレクトされるオブジェクトに関する情報が含まれています。

 [COR_HEAPINFO 構造体](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)列挙可能かどうかなど、ガベージ コレクション ヒープに関する全般情報を提供します。

 [COR_HEAPOBJECT 構造体](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープのオブジェクトに関する情報を提供します。

 [COR_IL_MAP](cor-il-map-structure.md)関数の相対的なオフセットの変更を指定します。

 [COR_SEGMENT 構造体](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)マネージ ヒープのメモリの領域に関する情報が含まれています。

 [COR_TYPEID 構造体](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)型識別子が含まれています。

 [COR_TYPE_LAYOUT 構造体](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)メモリ内のオブジェクトのレイアウトに関する情報を提供します。

 [COR_VERSION](cor-version-structure.md)共通言語ランタイムの標準的な 4 部構成のバージョン番号を格納します。

 [CorDebugBlockingObject 構造体](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)スレッドとスレッドがブロックされている理由の理由をブロックしているオブジェクトを定義します。

 [CorDebugEHClause 構造体](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)の中間言語 (IL) の特定の例外処理 (EH) 句を表します。

 [CorDebugExceptionObjectStackFrame 構造体](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)表しますスタック フレームの情報を例外オブジェクト。

 [CorDebugGuidToTypeMapping 構造体](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)マップ、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]を対応する GUID [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)オブジェクト。

 [DacpGetModuleAddress 構造](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md)モジュール アドレス要求のコンテナーを定義します。

 [DacpMethodDescData 構造](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md)トランスポートのバッファーをメソッドのランタイム情報を定義します。

 [DacpModuleData 構造](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md)トランスポートのバッファーをモジュールのランタイム情報を定義します。

 [DacpReJitData 構造](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md)プロファイラー インストルメント メソッドに関する基本情報を定義します。

 [StackTrace_SimpleContext 構造体](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)フルの代わりに使用できる単純なコンテキスト`CONTEXT`構造体。

## <a name="related-sections"></a>関連項目

 [デバッグ コクラス](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [デバッグ グローバル静的関数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
