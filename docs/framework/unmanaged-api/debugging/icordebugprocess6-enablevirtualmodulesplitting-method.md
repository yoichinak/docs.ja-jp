---
title: ICorDebugProcess6::EnableVirtualModuleSplitting メソッド
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb41cc47351ccf22fcd522b7d4291c235312bfaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167690"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting メソッド
仮想モジュール分割を有効または無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `enableSplitting`  
 `true` 仮想モジュール分割; を有効にするには`false`を無効にします。  
  
## <a name="remarks"></a>Remarks  
 仮想モジュール分割原因[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)ビルド中にマージされたモジュールが処理し、1 つの大規模なモジュールではなく、個別のモジュールのグループとして認識します。 さまざまな動作を変更してこれを行う[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)メソッドを以下に説明します。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
 このメソッドを呼び出し、`enableSplitting` の値をいつでも変更できます。 ステートフル関数変更は行われません、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)されているメソッドの動作を変更する以外のオブジェクト、[仮想モジュール分割とアンマネージ デバッグ Api](#APIs)呼び出された時点でセクション。 仮想モジュールを使用しても、これらのメソッドの呼び出し時にパフォーマンスの低下は発生しません。 さらに、仮想化されたメタデータのメモリ内キャッシュを大きな必要がありますを正しく実装する、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)仮想モジュール分割がオフになった後も、Api、およびこれらのキャッシュを保持可能性があります。  
  
## <a name="terminology"></a>用語  
 仮想モジュール分割について説明する場合には、次の用語が使用されます。  
  
 コンテナー モジュールまたはコンテナー  
 集計モジュール。  
  
 サブモジュール、または仮想モジュール  
 コンテナー内にあるモジュール。  
  
 標準モジュール  
 ビルド時にマージされなかったモジュール。 コンテナー モジュールでもサブモジュールでもありません。  
  
 ICorDebugModule インターフェイス オブジェクトでは、コンテナー モジュールとサブモジュールの両方が表されます。 ただし、インターフェイスの動作は、各ケースで若干異なりますとして、\<セクションを参照渡し x > セクションについて説明します。  
  
## <a name="modules-and-assemblies"></a>モジュールとアセンブリ  
 アセンブリ マージ シナリオではマルチモジュール アセンブリはサポートされないため、モジュールとアセンブリの間には一対一リレーションシップがあります。 コンテナー モジュールまたはサブモジュールを表すかどうかに関係なく、各 ICorDebugModule オブジェクトには、対応する ICorDebugAssembly オブジェクトがあります。 [Icordebugmodule::getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)メソッドが、モジュールからアセンブリに変換します。 その他の方向にマップする、 [icordebugassembly::enumeratemodules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)メソッドは、1 つだけのモジュールを列挙します。 この場合、アセンブリとモジュールは緊密に結合されたペアとなるため、アセンブリとモジュールはほぼ同義の用語となります。  
  
## <a name="behavioral-differences"></a>動作の違い  
 コンテナー モジュールには、次の動作と特性があります。  
  
-   構成要素であるすべてのサブモジュールのメタデータはマージされます。  
  
-   型名は変形する可能性があります。  
  
-   [Icordebugmodule::getname](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)メソッドが、ディスク上のモジュールへのパスを返します。  
  
-   [Icordebugmodule::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)メソッドは、そのイメージのサイズを返します。  
  
-   ICorDebugAssembly3.EnumerateContainedAssemblies メソッドは、サブモジュールを一覧表示します。  
  
-   ICorDebugAssembly3.GetContainerAssembly メソッドは、`S_FALSE` を返します。  
  
 サブモジュールには、次の動作と特性があります。  
  
-   マージされた元のアセンブリのみに対応する削減されたメタデータのセットがあります。  
  
-   メタデータ名は、変形しません。  
  
-   メタデータ トークンは、ビルド プロセスでマージされる前の元のアセンブリ内のトークンと一致することはほとんどありません。  
  
-   [Icordebugmodule::getname](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)メソッドは、アセンブリ名、ファイル パスではなくを返します。  
  
-   [Icordebugmodule::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)メソッドは元のマージされていないイメージのサイズを返します。  
  
-   ICorDebugModule3.EnumerateContainedAssemblies メソッドは、`S_FALSE` を返します。  
  
-   ICorDebugAssembly3.GetContainerAssembly メソッドは、格納しているモジュールを返します。  
  
## <a name="interfaces-retrieved-from-modules"></a>モジュールから取得されるインターフェイス  
 さまざまなインターフェイスをモジュールから作成または取得できます。 その例には次のものがあります。  
  
-   ICorDebugClass オブジェクトによって返される、 [icordebugmodule::getclassfromtoken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)メソッド。  
  
-   ICorDebugAssembly オブジェクトによって返される、 [icordebugmodule::getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)メソッド。  
  
 これらのオブジェクトは常にキャッシュ[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)、し、同じポインター id が作成またはコンテナー モジュールまたはサブモジュールからクエリを実行するのかどうかに関係なく必要があります。 サブモジュールは、独自のコピーを持つ個別のキャッシュではなく、これらのキャッシュされたオブジェクトのフィルター処理されたビューを提供します。  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>仮想モジュール分割とアンマネージ デバッグ API  
 次の表に、仮想モジュール分割がアンマネージ デバッグ API の他のメソッドの動作に影響する方法を示します。  
  
|メソッド|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|この関数が最初に定義されたサブモジュールを返します|この関数がマージされたコンテナー モジュールを返します|  
|[ICorDebugClass::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|このクラスが最初に定義されたサブモジュールを返します。|このクラスがマージされたコンテナー モジュールを返します。|  
|ICorDebugModuleDebugEvent::GetModule|読み込まれたコンテナー モジュールを返します。 サブモジュールは、この設定に関係なく、読み込みイベントを提供されません。|読み込まれたコンテナー モジュールを返します。|  
|[ICorDebugAppDomain::EnumerateAssemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|サブアセンブリと標準アセンブリのリストを返します。コンテナー アセンブリは含まれません。 **注:** いずれかのコンテナー アセンブリにシンボルがない場合、そのサブアセンブリは列挙されません。 いずれかの標準アセンブリにシンボルがない場合、列挙される場合と列挙されない場合があります。|コンテナー アセンブリと標準アセンブリのリストを返します。サブアセンブリは含まれません。 **注:** いずれかの標準アセンブリにシンボルがない場合、列挙される場合と列挙されない場合があります。|  
|[Icordebugcode::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (IL コードのみを参照する) とき|マージ前のアセンブリ イメージ内で有効な IL を返します。 具体的には、参照先の型が IL を含む仮想モジュールで定義されていない場合、インライン メタデータ トークンは正確に TypeRef または MemberRef トークンになります。 これらの TypeRef または MemberRef トークンで検索できる、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)の対応する仮想 ICorDebugModule オブジェクトのオブジェクト。|マージ後のアセンブリ イメージ内の IL を返します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess6 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
