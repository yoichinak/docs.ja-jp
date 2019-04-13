---
title: ICorDebugSymbolProvider インターフェイス
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc33018f68f9634a29e2f5c52123a0215b446de7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228966"
---
# <a name="icordebugsymbolprovider-interface"></a>ICorDebugSymbolProvider インターフェイス
デバッグ シンボル情報を取得するために使用できるメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetAssemblyImageBytes メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|マージされたアセンブリ内の指定の相対仮想アドレス (RVA: relative virtual address) で、マージされたアセンブリのデータを読み取ります。|  
|[GetAssemblyImageMetadata メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|マージされたアセンブリのメタデータを返します。|  
|[GetCodeRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|メソッド内の指定の相対仮想アドレス (RVA: relative virtual address) で、メソッド開始アドレスとサイズを取得します。|  
|[GetInstanceFieldSymbols メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|typespec シグネチャに対応するインスタンス フィールド シンボルを取得します。|  
|[GetMergedAssemblyRecords メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|すべてのマージされたアセンブリのシンボル レコードを取得します。|  
|[GetMethodLocalSymbols メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのローカル シンボルを取得します。|  
|[GetMethodParameterSymbols メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|メソッドの指定の相対仮想アドレス (RVA: relative virtual address ) で、そのメソッドのパラメーター シンボルを取得します。|  
|[GetMethodProps メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのプロパティに関する情報 (メソッドのメタデータ トークンなど) と、そのジェネリック パラメーターに関する情報を返します。|  
|[GetObjectSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|typespec シグネチャに基づいてオブジェクトのオブジェクト サイズを返します。|  
|[GetStaticFieldSymbols メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|typespec シグネチャに対応する静的フィールド シンボルを取得します。|  
|[GetTypeProps メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|Vtable の指定の相対仮想アドレス (RVA) における、ジェネリック パラメーターのシグネチャの数などの型のプロパティに関する情報を返します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このインターフェイスは .NET ネイティブでのみ使用可能です。 .NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
