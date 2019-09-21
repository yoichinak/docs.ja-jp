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
ms.openlocfilehash: b830af5d59c0eb177d815451ecedbdc14121aaad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964757"
---
# <a name="icordebugtype-interface"></a>ICorDebugType インターフェイス
基本または複合 (つまり、ユーザー定義) のいずれかの型を表します。 型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateTypeParameters メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<xref:System.Type> この`ICorDebugType`によって参照されるクラスのジェネリックパラメーターを参照する、ツールのインターフェイスポインターを取得します。|  
|[GetBase メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|`ICorDebugType` この`ICorDebugType`によって参照されるクラス (存在する場合) の基本クラスを参照するへのインターフェイスポインターを取得します。|  
|[GetClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|この`ICorDebugType`の型指定されたコンストラクターを参照する、によるクラスへのインターフェイスポインターを取得します。|  
|[GetFirstTypeParameter メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|この<xref:System.Type> `ICorDebugType` によって参照されるクラスのコンストラクターの最初のジェネリックパラメーターを参照するへのインターフェイスポインターを取得します。`ICorDebugType`|  
|[GetRank メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|配列型の次元数を取得します。|  
|[GetStaticFieldValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|指定したスタックフレーム内の指定したフィールドトークンによって参照される静的フィールドの値を格納する、ICorDebugValue へのインターフェイスポインターを取得します。|  
|[GetType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<xref:System.Type> この`ICorDebugType`によって参照される共通言語ランタイムのネイティブ型を記述する corelementtype 値を取得します。|  
  
## <a name="remarks"></a>Remarks  
 型がジェネリックの場合、 `ICorDebugClass`はインスタンス型を表します。 インターフェイス`ICorDebugType`は、インスタンス化されたジェネリック型を表します。 たとえば、ハッシュテーブル\<K、V > はで`ICorDebugClass`表されますが、\<hashtable Int32、String > はによっ`ICorDebugType`て表されます。  
  
 非ジェネリック型は、と`ICorDebugClass` `ICorDebugType`の両方で表されます。 後者のインターフェイスは、型のインスタンス化を処理するために .NET Framework バージョン2.0 で導入されました。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
