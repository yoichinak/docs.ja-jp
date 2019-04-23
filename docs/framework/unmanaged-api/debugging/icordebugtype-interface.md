---
title: ICorDebugType インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74863af1096f8600b8095e593c1f3c820c512e9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166804"
---
# <a name="icordebugtype-interface"></a>ICorDebugType インターフェイス
型、基本または複雑な (つまり、ユーザー定義) を表します。 型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateTypeParameters メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|ジェネリックを参照する、ICorDebugTypeEnum へのインターフェイス ポインターを取得<xref:System.Type>これによって参照されるクラスのパラメーター`ICorDebugType`します。|  
|[GetBase メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|インターフェイス ポインターを取得、`ICorDebugType`これによって参照されるクラスの基底クラスを参照する`ICorDebugType`が存在する場合は、します。|  
|[GetClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|この型指定されたコンス トラクターを参照する、ICorDebugClass へのインターフェイス ポインターを取得`ICorDebugType`します。|  
|[GetFirstTypeParameter メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|インターフェイス ポインターを取得、`ICorDebugType`を参照する最初のジェネリック<xref:System.Type>これによって参照されるクラスのコンス トラクターのパラメーター`ICorDebugType`します。|  
|[GetRank メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|配列型の次元数を取得します。|  
|[GetStaticFieldValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|指定したスタック フレームでトークンを指定したフィールドによって参照される静的フィールドの値を格納インターフェイス ポインターを取得します。|  
|[GetType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|共通言語ランタイムのネイティブな型を記述する CorElementType 値を取得します<xref:System.Type>これによって参照される`ICorDebugType`します。|  
  
## <a name="remarks"></a>Remarks  
 場合は、型がジェネリック`ICorDebugClass`インスタンス化されていない型を表します。 `ICorDebugType`インターフェイスはジェネリック型のインスタンスを表します。 たとえば、ハッシュ テーブル\<K, V > で表されます`ICorDebugClass`一方、ハッシュ テーブル\<Int32, String > で表されます`ICorDebugType`します。  
  
 非ジェネリック型は型が両方によって表される`ICorDebugClass`と`ICorDebugType`します。 後者のインターフェイスは、型のインスタンス化を処理するには、.NET Framework version 2.0 で導入されました。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
