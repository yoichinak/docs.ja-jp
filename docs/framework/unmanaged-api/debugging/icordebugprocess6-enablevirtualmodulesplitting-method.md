---
title: ICorDebugProcess6::EnableVirtualModuleSplitting メソッド
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bd06dd3f58a1f74fbdb5ec61c4896f5c1696856
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931058"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting メソッド
仮想モジュール分割を有効または無効にします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `enableSplitting`  
 仮想モジュール分割を有効にするには、`true`。無効にするには、`false`。  
  
## <a name="remarks"></a>Remarks  
 仮想モジュール分割により、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)は、ビルド処理中にマージされたモジュールを認識し、1つの大きなモジュールではなく個別のモジュールのグループとして表示します。 これにより、以下で説明するさまざまな[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)メソッドの動作が変更されます。  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
 このメソッドを呼び出し、`enableSplitting` の値をいつでも変更できます。 このメソッドは、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)オブジェクトでステートフルな機能変更を発生させません。これは、[仮想モジュール分割とアンマネージデバッグ api](#APIs)セクションに示されているメソッドの動作を、呼び出されたときに変更することではありません。 仮想モジュールを使用しても、これらのメソッドの呼び出し時にパフォーマンスの低下は発生しません。 また、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) api を正しく実装するために、仮想化されたメタデータの大量のメモリ内キャッシュが必要になる場合があります。これらのキャッシュは、仮想モジュールの分割がオフになった後でも保持される可能性があります。  
  
## <a name="terminology"></a>用語  
 仮想モジュール分割について説明する場合には、次の用語が使用されます。  
  
 コンテナー モジュールまたはコンテナー  
 集計モジュール。  
  
 サブモジュール、または仮想モジュール  
 コンテナー内にあるモジュール。  
  
 標準モジュール  
 ビルド時にマージされなかったモジュール。 コンテナー モジュールでもサブモジュールでもありません。  
  
 コンテナーモジュールとサブモジュールは両方とも、モジュールインターフェイスオブジェクトによって表されます。 ただし、インターフェイスの動作は、各ケースでは、セクション > セクションで\<説明するように、それぞれ少し異なります。  
  
## <a name="modules-and-assemblies"></a>モジュールとアセンブリ  
 アセンブリ マージ シナリオではマルチモジュール アセンブリはサポートされないため、モジュールとアセンブリの間には一対一リレーションシップがあります。 各モジュールオブジェクトは、コンテナーモジュールを表しているか、サブモジュールであるかに関係なく、それぞれに対応する "オブジェクト" を持ちます。 のモジュール[:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)メソッドは、モジュールからアセンブリに変換します。 他の方向にマップするために、"コードの[アセンブリ:: 列挙体](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)" メソッドは1つのモジュールのみを列挙します。 この場合、アセンブリとモジュールは緊密に結合されたペアとなるため、アセンブリとモジュールはほぼ同義の用語となります。  
  
## <a name="behavioral-differences"></a>動作の違い  
 コンテナー モジュールには、次の動作と特性があります。  
  
- 構成要素であるすべてのサブモジュールのメタデータはマージされます。  
  
- 型名は変形する可能性があります。  
  
- [モジュール:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)メソッドは、ディスク上のモジュールへのパスを返します。  
  
- [モジュール:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)メソッドは、そのイメージのサイズを返します。  
  
- ICorDebugAssembly3.EnumerateContainedAssemblies メソッドは、サブモジュールを一覧表示します。  
  
- ICorDebugAssembly3.GetContainerAssembly メソッドは、`S_FALSE` を返します。  
  
 サブモジュールには、次の動作と特性があります。  
  
- マージされた元のアセンブリのみに対応する削減されたメタデータのセットがあります。  
  
- メタデータ名は、変形しません。  
  
- メタデータ トークンは、ビルド プロセスでマージされる前の元のアセンブリ内のトークンと一致することはほとんどありません。  
  
- [モジュール:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)メソッドは、ファイルパスではなく、アセンブリ名を返します。  
  
- は、マージさ[れてい](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)ない元のイメージのサイズを返します。  
  
- ICorDebugModule3.EnumerateContainedAssemblies メソッドは、`S_FALSE` を返します。  
  
- ICorDebugAssembly3.GetContainerAssembly メソッドは、格納しているモジュールを返します。  
  
## <a name="interfaces-retrieved-from-modules"></a>モジュールから取得されるインターフェイス  
 さまざまなインターフェイスをモジュールから作成または取得できます。 その例には次のものがあります。  
  
- には、[モジュール:: GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)メソッドによって返される、のオブジェクト。  
  
- [モジュール:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)メソッドによって返される、オブジェクト。  
  
 これらのオブジェクトは常に[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)によってキャッシュされ、コンテナーモジュールまたはサブモジュールで作成または照会されたかどうかに関係なく、同じポインター id を持ちます。 サブモジュールは、独自のコピーを持つ個別のキャッシュではなく、これらのキャッシュされたオブジェクトのフィルター処理されたビューを提供します。  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>仮想モジュール分割とアンマネージ デバッグ API  
 次の表に、仮想モジュール分割がアンマネージ デバッグ API の他のメソッドの動作に影響する方法を示します。  
  
|メソッド|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|この関数が最初に定義されたサブモジュールを返します|この関数がマージされたコンテナー モジュールを返します|  
|[ICorDebugClass::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|このクラスが最初に定義されたサブモジュールを返します。|このクラスがマージされたコンテナー モジュールを返します。|  
|ICorDebugModuleDebugEvent::GetModule|読み込まれたコンテナー モジュールを返します。 サブモジュールは、この設定に関係なく、読み込みイベントを提供されません。|読み込まれたコンテナー モジュールを返します。|  
|[EnumerateAssemblies Appdomain::](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|サブアセンブリと標準アセンブリのリストを返します。コンテナー アセンブリは含まれません。 **注:** いずれかのコンテナー アセンブリにシンボルがない場合、そのサブアセンブリは列挙されません。 いずれかの標準アセンブリにシンボルがない場合、列挙される場合と列挙されない場合があります。|コンテナー アセンブリと標準アセンブリのリストを返します。サブアセンブリは含まれません。 **注:** いずれかの標準アセンブリにシンボルがない場合、列挙される場合と列挙されない場合があります。|  
|[コード例:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)(IL コードのみを参照している場合)|マージ前のアセンブリ イメージ内で有効な IL を返します。 具体的には、参照先の型が IL を含む仮想モジュールで定義されていない場合、インライン メタデータ トークンは正確に TypeRef または MemberRef トークンになります。 これらの TypeRef または MemberRef トークンは、対応する仮想 ICorDebugModule モジュールオブジェクトの [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) オブジェクトで検索できます。|マージ後のアセンブリ イメージ内の IL を返します。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess6 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
