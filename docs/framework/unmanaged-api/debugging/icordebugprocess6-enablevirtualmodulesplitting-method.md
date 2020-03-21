---
title: ICorDebugProcess6::EnableVirtualModuleSplitting メソッド
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 8ad15d11ce81323b30434b3db98259a74a198f29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178572"
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
  
## <a name="remarks"></a>解説  
 仮想モジュールの分割により[、ICorDebug](icordebug-interface.md)はビルドプロセス中にマージされたモジュールを認識し、それらを 1 つの大きなモジュールではなく、個別のモジュールのグループとして表示します。 これにより、以下に説明するさまざまな[ICorDebug](icordebug-interface.md)メソッドの動作が変更されます。  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
 このメソッドを呼び出し、`enableSplitting` の値をいつでも変更できます。 呼び出された時点で[の仮想モジュールの分割とアンマネージ デバッグ API](#APIs)セクションに記載されているメソッドの動作を変更する以外に[、ICorDebug](icordebug-interface.md)オブジェクトのステートフルな関数の変更は発生しません。 仮想モジュールを使用しても、これらのメソッドの呼び出し時にパフォーマンスの低下は発生しません。 さらに[、IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) API を正しく実装するために、仮想化されたメタデータのメモリ内キャッシュが重要になる場合があり、仮想モジュールの分割がオフになっていても、これらのキャッシュは保持される場合があります。  
  
## <a name="terminology"></a>用語  
 仮想モジュール分割について説明する場合には、次の用語が使用されます。  
  
 コンテナー モジュールまたはコンテナー  
 集計モジュール。  
  
 サブモジュール、または仮想モジュール  
 コンテナー内にあるモジュール。  
  
 標準モジュール  
 ビルド時にマージされなかったモジュール。 コンテナー モジュールでもサブモジュールでもありません。  
  
 コンテナー モジュールとサブモジュールは、どちらも ICorDebugModuleインターフェイス オブジェクトによって表されます。 ただし、このセクションで説明しているように、インターフェイスの動作は>、\<各ケースで若干異なります。  
  
## <a name="modules-and-assemblies"></a>モジュールとアセンブリ  
 アセンブリ マージ シナリオではマルチモジュール アセンブリはサポートされないため、モジュールとアセンブリの間には一対一リレーションシップがあります。 各 ICorDebugModule オブジェクトには、コンテナー モジュールを表すかサブモジュールを表すかに関係なく、対応する ICorDebugAssembly オブジェクトがあります。 メソッドは[モジュール](icordebugmodule-getassembly-method.md)からアセンブリに変換されます。 他の方向にマップするには[、ICorDebugAssembly::列挙モジュール](icordebugassembly-enumeratemodules-method.md)メソッドは 1 つのモジュールのみを列挙します。 この場合、アセンブリとモジュールは緊密に結合されたペアとなるため、アセンブリとモジュールはほぼ同義の用語となります。  
  
## <a name="behavioral-differences"></a>動作の違い  
 コンテナー モジュールには、次の動作と特性があります。  
  
- 構成要素であるすべてのサブモジュールのメタデータはマージされます。  
  
- 型名は変形する可能性があります。  
  
- メソッドは[、](icordebugmodule-getname-method.md)ディスク上のモジュールへのパスを返します。  
  
- メソッドは[、](icordebugmodule-getsize-method.md)そのイメージのサイズを返します。  
  
- ICorDebugAssembly3.EnumerateContainedAssemblies メソッドは、サブモジュールを一覧表示します。  
  
- ICorDebugAssembly3.GetContainerAssembly メソッドは、`S_FALSE` を返します。  
  
 サブモジュールには、次の動作と特性があります。  
  
- マージされた元のアセンブリのみに対応する削減されたメタデータのセットがあります。  
  
- メタデータ名は、変形しません。  
  
- メタデータ トークンは、ビルド プロセスでマージされる前の元のアセンブリ内のトークンと一致することはほとんどありません。  
  
- メソッドは[、](icordebugmodule-getname-method.md)ファイル パスではなくアセンブリ名を返します。  
  
- メソッドは[、](icordebugmodule-getsize-method.md)元のマージされていないイメージ サイズを返します。  
  
- ICorDebugModule3.EnumerateContainedAssemblies メソッドは、`S_FALSE` を返します。  
  
- ICorDebugAssembly3.GetContainerAssembly メソッドは、格納しているモジュールを返します。  
  
## <a name="interfaces-retrieved-from-modules"></a>モジュールから取得されるインターフェイス  
 さまざまなインターフェイスをモジュールから作成または取得できます。 たとえば、次のようなシナリオがあります。  
  
- [メソッドによって](icordebugmodule-getclassfromtoken-method.md)返されるオブジェクト。  
  
- [メソッドによって](icordebugmodule-getassembly-method.md)返されるオブジェクト。  
  
 これらのオブジェクトは常に[ICorDebug](icordebug-interface.md)によってキャッシュされ、コンテナー モジュールまたはサブモジュールから作成またはクエリされたかどうかにかかわらず、同じポインター ID を持ちます。 サブモジュールは、独自のコピーを持つ個別のキャッシュではなく、これらのキャッシュされたオブジェクトのフィルター処理されたビューを提供します。  
  
<a name="APIs"></a>
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>仮想モジュール分割とアンマネージ デバッグ API  
 次の表に、仮想モジュール分割がアンマネージ デバッグ API の他のメソッドの動作に影響する方法を示します。  
  
|Method|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](icordebugfunction-getmodule-method.md)|この関数が最初に定義されたサブモジュールを返します|この関数がマージされたコンテナー モジュールを返します|  
|[ICorDebugClass::GetModule](icordebugclass-getmodule-method.md)|このクラスが最初に定義されたサブモジュールを返します。|このクラスがマージされたコンテナー モジュールを返します。|  
|ICorDebugModuleDebugEvent::GetModule|読み込まれたコンテナー モジュールを返します。 サブモジュールは、この設定に関係なく、読み込みイベントを提供されません。|読み込まれたコンテナー モジュールを返します。|  
|[ICorDebugAppDomain::EnumerateAssemblies](icordebugappdomain-enumerateassemblies-method.md)|サブアセンブリと標準アセンブリのリストを返します。コンテナー アセンブリは含まれません。 **注:** コンテナー アセンブリにシンボルが見つからない場合、そのサブアセンブリは列挙されません。 いずれかの標準アセンブリにシンボルがない場合、列挙される場合と列挙されない場合があります。|コンテナー アセンブリと標準アセンブリのリストを返します。サブアセンブリは含まれません。 **注:** 通常のアセンブリにシンボルが見つからない場合は、列挙される場合と、列挙されない場合があります。|  
|[ICorデバッグコード::GetCode](icordebugcode-getcode-method.md) (ILコードのみを参照する場合)|マージ前のアセンブリ イメージ内で有効な IL を返します。 具体的には、参照先の型が IL を含む仮想モジュールで定義されていない場合、インライン メタデータ トークンは正確に TypeRef または MemberRef トークンになります。 これらの型参照またはメンバー参照トークンは、対応する仮想 ICorDebugModule オブジェクトの[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)オブジェクトで検索できます。|マージ後のアセンブリ イメージ内の IL を返します。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess6 インターフェイス](icordebugprocess6-interface.md)
- [デバッグ インターフェイス](debugging-interfaces.md)
