---
title: メタデータ列挙体
ms.date: 03/30/2017
helpviewer_keywords:
- enumerations [.NET Framework metadata]
- metadata enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], metadata
ms.assetid: 711ab251-cfdb-4280-aaa6-9bc1b341cdc3
ms.openlocfilehash: 92f2419070738a49f78c1f1497652cc0b89f3b21
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447867"
---
# <a name="metadata-enumerations"></a>メタデータ列挙体
このセクションでは、メタデータ API が使用するアンマネージ列挙について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [AssemblyFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)  
 アセンブリのランタイム機能を記述する値が格納されます。  
  
 [AssemblyRefFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)  
 アセンブリ参照の機能を記述する値が格納されます。  
  
 [CeeSectionAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/ceesectionattr-enumeration.md)  
 Provides values that specify the attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.  
  
 [CeeSectionRelocType 列挙型](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)  
 Provides values to influence the type of `reloc` instruction emitted in a call to the [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md) method.  
  
 [COINITICOR 列挙型](../../../../docs/framework/unmanaged-api/metadata/coiniticor-enumeration.md)  
 Specifies constants used by [CoInitializeCor](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md) when initializing the common language runtime.  
  
 [COINITIEE 列挙型](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)  
 Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.  
  
 [CorArgType 列挙型](../../../../docs/framework/unmanaged-api/metadata/corargtype-enumeration.md)  
 ランタイム ハンドルのネイティブな型を記述する値が格納されます。  
  
 [CorAssemblyFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)  
 アセンブリ コンパイルに適用されるメタデータを記述する値が格納されます。  
  
 [CorAttributeTargets 列挙型](../../../../docs/framework/unmanaged-api/metadata/corattributetargets-enumeration.md)  
 属性を適用できるアプリケーション要素を指定します。  
  
 [CorCallingConvention 列挙型](../../../../docs/framework/unmanaged-api/metadata/corcallingconvention-enumeration.md)  
 マネージド コードで作成される呼び出し規則のタイプを記述する値が格納されます。  
  
 [CorCheckDuplicatesFor 列挙型](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md)  
 重複の確認で使用される値が格納されます。  
  
 [CorDeclSecurity 列挙型](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md)  
 共通言語ランタイムによって使用される宣言セキュリティの型を記述する値が格納されます。  
  
 CorElementType  
 共通言語ランタイム <xref:System.Type> の基となるネイティブ型を示す値が格納されます。  
  
 [CorErrorIfEmitOutOfOrder 列挙型](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md)  
 メタデータの生成順序が不適切である場合にエラー メッセージが生成される条件を示すフラグ値が格納されます。  
  
 [CorEventAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/coreventattr-enumeration.md)  
 イベントのメタデータを記述する値が格納されます。  
  
 [CorFieldAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/corfieldattr-enumeration.md)  
 フィールドについてのメタデータを記述する値が格納されます。  
  
 [CorFileFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)  
 Contains values that describe the type of file defined in a call to the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.  
  
 [CorFileMapping 列挙型](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)  
 Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.  
  
 [CorGenericParamAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)  
 Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to the [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md) method.  
  
 [CorImportOptions 列挙型](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)  
 現在のスコープ外のアセンブリのインポート中の動作を制御するフラグ値が格納されます。  
  
 [CorLinkerOptions 列挙型](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md)  
 メタデータ リンカーのオプションを選択するためのフラグを指定します。  
  
 [CorLocalRefPreservation 列挙型](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md)  
 ローカル参照の処理のためのフラグ値が格納されます。  
  
 [CorManifestResourceFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)  
 アセンブリ マニフェストでエンコードされているリソースの参照範囲を記述する値が格納されます。  
  
 [CorMethodAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)  
 メソッドについてのメタデータを記述する値が格納されます。  
  
 [CorMethodImpl 列挙型](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)  
 メソッド実装の機能を記述する値が格納されます。  
  
 [CorMethodSemanticsAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md)  
 メソッドとそれに関連付けられているプロパティまたはイベントとの関係を記述する値が格納されます。  
  
 [CorNativeLinkFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)  
 ネイティブ コードをリンクするときに、リンカーが使用するフラグ値を提供します。  
  
 [CorNativeLinkType 列挙型](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)  
 ネイティブ コード内のリンクの種類を示す値を提供します。  
  
 [CorNativeType 列挙型](../../../../docs/framework/unmanaged-api/metadata/cornativetype-enumeration.md)  
 ネイティブのアンマネージ型を記述する値が格納されます。  
  
 [CorNotificationForTokenMovement 列挙型](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)  
 トークンの移動時の通知に影響するフラグの値が格納されます。  
  
 [CorOpenFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)  
 マニフェスト ファイルを開くときにメタデータの動作を制御するフラグ値を含めます。  
  
 [CorParamAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/corparamattr-enumeration.md)  
 メソッド パラメーターのメタデータを記述する値が格納されます。  
  
 [CorPEKind 列挙型](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)  
 Contains values that describe a portable executable file, as returned from a call to the [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md) method.  
  
 [CorPinvokeMap 列挙型](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md)  
 PInvoke 呼び出しの機能を記述する値が格納されます。  
  
 [CorPropertyAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)  
 プロパティのメタデータを記述する値が格納されます。  
  
 [CorRefToDefCheck 列挙型](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)  
 コードを最適化するために定義に変換される、参照先アイテムを制御するフラグを指定します。  
  
 [CorRegFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/corregflags-enumeration.md)  
 モジュールまたは複合イメージをインストールするときに登録に使用するフラグ値を提供します。  
  
 [CorSaveSize 列挙型](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)  
 保存操作のサイズの照会で要求される精度のレベルを示す値が格納されます。  
  
 [CorSerializationType 列挙型](../../../../docs/framework/unmanaged-api/metadata/corserializationtype-enumeration.md)  
 共通言語ランタイムがオブジェクトをシリアル化する方法を記述する値が格納されます。 These values generally correspond to CorElementType values.  
  
 [CorSetENC 列挙型](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md)  
 メタデータの生成中の動作を決定する値が格納されます。  
  
 [CorThreadSafetyOptions 列挙型](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md)  
 スレッド セーフのオプションを選択するためのフラグを指定します。  
  
 [CorTokenType 列挙型](../../../../docs/framework/unmanaged-api/metadata/cortokentype-enumeration.md)  
 メタデータ トークンが参照するオブジェクトの種類を示す値が格納されます。  
  
 [CorTypeAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)  
 メタデータ型を示す値が格納されます。  
  
 [CorUnmanagedCallingConvention 列挙型](../../../../docs/framework/unmanaged-api/metadata/corunmanagedcallingconvention-enumeration.md)  
 アンマネージ呼び出し規約を記述する値が格納されます。  
  
 [CorValidatorModuleType 列挙型](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md)  
 Provides values used by the [IMetaDataValidate](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md) interface to specify the type of the module (PE file vs. .obj file).  
  
 [COUNINITIEE 列挙型](../../../../docs/framework/unmanaged-api/metadata/couninitiee-enumeration.md)  
 Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.  
  
## <a name="related-sections"></a>関連項目  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
  
 [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [メタデータ構造体](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [メタデータ共用体](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
