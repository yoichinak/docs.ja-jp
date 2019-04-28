---
title: ICorDebugClass2::GetParameterizedType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e1734ca91fd48cc15b8dbf25f11518ed0455b6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750775"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType メソッド
このクラスの型宣言を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `elementType`  
 [in]このクラスの要素の型を指定する CorElementType 列挙型の値:この ICorDebugClass2 が値型を表している場合は、この値を ELEMENT_TYPE_VALUETYPE に設定します。 この場合、この値を ELEMENT_TYPE_CLASS に設定`ICorDebugClass2`複合型を表します。  
  
 `nTypeArgs`  
 [in]型がジェネリックの場合、型パラメーターの数。 型パラメーター (ある場合) の数は、クラスに必要な数と一致する必要があります。  
  
 `ppTypeArgs`  
 [in]型パラメーターを表す ICorDebugType オブジェクトを指す各ポインターの配列。 クラスが非ジェネリックの場合は、この値が null です。  
  
 `ppType`  
 [out]アドレスへのポインター、`ICorDebugType`型宣言を表すオブジェクト。 このオブジェクトが等しく、<xref:System.Type>マネージ コード内のオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 クラスは非ジェネリックは、型のパラメーターが存在しない場合`GetParameterizedType`単にクラスに対応するランタイム型のオブジェクトを取得します。 `elementType`クラスの適切な要素の型にパラメーターを設定する必要があります。ELEMENT_TYPE_VALUETYPE クラスが値型である場合それ以外の場合、ELEMENT_TYPE_CLASS します。  
  
 クラスが型パラメーターを受け入れる場合 (たとえば、 `ArrayList<T>`)、使用することができます`GetParameterizedType`などの型のインスタンスの型のオブジェクトを構築する`ArrayList<int>`します。  
  
## <a name="background-information"></a>背景情報  
 .NET Framework バージョン 1.0 および 1.1 では、メタデータ内のすべての型を直接実行中のプロセス内の型にマップする。 したがって、メタデータの種類と、ランタイム型は、実行中のプロセスで 1 つの表現必要があります。 ただし、メタデータ内の 1 つのジェネリック型は、実行中のプロセスでの型の複数の異なるインスタンスにマップできます。 たとえば、メタデータ型`SortedList<K,V>`にマップできます`SortedList<String, EmployeeRecord>`、 `SortedList<Int32, String>`、`SortedList<String,Array<Int32>>`など。 そのため、型のインスタンス化を処理する方法をする必要があります。  
  
 .NET Framework version 2.0 では、`ICorDebugType`インターフェイス。 ジェネリック型の場合、`ICorDebugClass`または`ICorDebugClass2`オブジェクトがインスタンス化されていない型を表します (`SortedList<K,V>`)、および`ICorDebugType`オブジェクトは、さまざまなインスタンス化された型を表します。 指定された、`ICorDebugClass`または`ICorDebugClass2`オブジェクトを作成することができます、`ICorDebugType`オブジェクトのすべてのインスタンス化を呼び出して、`ICorDebugClass2::GetParameterizedType`メソッド。 作成することも、 `ICorDebugType` Int32 などの単純型または非ジェネリックの種類のオブジェクト。  
  
 導入に伴い、`ICorDebugType`型の実行時の概念を表すオブジェクトが、API 全体に影響します。 かかっていた関数、`ICorDebugClass`または`ICorDebugClass2`オブジェクトまたはであっても、`CorElementType`を値が汎用化されて、`ICorDebugType`オブジェクト。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
