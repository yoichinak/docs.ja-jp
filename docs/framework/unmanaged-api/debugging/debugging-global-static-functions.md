---
title: デバッグ グローバル静的関数
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2403d736d031aab52525fc12b5071e764a8bde1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698526"
---
# <a name="debugging-global-static-functions"></a>デバッグ グローバル静的関数
このセクションでは、デバッグ API が使用するアンマネージ グローバル静的関数について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [_EFN_GetManagedExcepStack 関数](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 指定したマネージド例外オブジェクトのアドレスに応じて、中に含まれているスタック トレースの文字列バージョンを返します。  
  
 [_EFN_GetManagedObjectFieldInfo 関数](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 指定したオブジェクト ポインターとフィールド名を使用して、オブジェクトの先頭からフィールドまでのオフセットとフィールドの値を取得します。  
  
 [_EFN_GetManagedObjectName 関数](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 指定したマネージド オブジェクトのポインターを使用して、型の名前を取得します。  
  
 [_EFN_StackTrace 関数](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 マネージド スタック トレースのテキスト表現および `CONTEXT` レコードの配列 (アンマネージド コードとマネージド コードの間の各移行につき 1 つ) を提供します。  
  
 [CLRDataCreateInstance 関数](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 指定した対象プロセスの指定したインターフェイス オブジェクトを作成するために、共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。  
  
 [PFN_CLRDataCreateInstance 関数ポインター](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 指定した対象プロセスの指定したインターフェイス オブジェクトを作成するために、CLR データ アクセス サービスによって呼び出される関数を指します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッグ コクラス](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
