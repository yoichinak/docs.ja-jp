---
title: メタデータ列挙体
ms.date: 03/30/2017
helpviewer_keywords:
- enumerations [.NET Framework metadata]
- metadata enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], metadata
ms.assetid: 711ab251-cfdb-4280-aaa6-9bc1b341cdc3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f92b87cc2748a709361ff2c0c8129db5f7fe6046
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042199"
---
# <a name="metadata-enumerations"></a>メタデータ列挙体
このセクションでは、メタデータ API が使用するアンマネージ列挙について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [AssemblyFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)  
 アセンブリのランタイム機能を記述する値が格納されます。  
  
 [AssemblyRefFlags 列挙型](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)  
 アセンブリ参照の機能を記述する値が格納されます。  
  
 [CeeSectionAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/ceesectionattr-enumeration.md)  
 使用するセクションの属性を指定する値を提供、 [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)インターフェイス。  
  
 [CeeSectionRelocType 列挙型](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)  
 種類に影響する値を提供`reloc`への呼び出しで出力される命令、 [iceegen::addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)メソッド。  
  
 [COINITICOR 列挙型](../../../../docs/framework/unmanaged-api/metadata/coiniticor-enumeration.md)  
 使用される定数を指定します[CoInitializeCor](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)共通言語ランタイムを初期化するときにします。  
  
 [COINITIEE 列挙型](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)  
 使用される定数を指定します[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)共通言語ランタイムを初期化するときにします。  
  
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
 呼び出しで定義されているファイルの種類を記述する値が含まれています、 [imetadataassemblyemit::definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)メソッド。  
  
 [CorFileMapping 列挙型](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)  
 呼び出しから返されるファイル マッピングの種類を記述する値が含まれています、 [imetadatainfo::getfilemapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)メソッド。  
  
 [CorGenericParamAttr 列挙型](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)  
 記述する値が含まれています、<xref:System.Type>の呼び出しで使用される、ジェネリック型パラメーター、 [imetadataemit 2::definegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)メソッド。  
  
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
 呼び出しから返されるように、ポータブル実行可能ファイルを記述する値が含まれています、 [imetadataimport 2::getpekind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)メソッド。  
  
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
 共通言語ランタイムがオブジェクトをシリアル化する方法を記述する値が格納されます。 これらの値は、一般に、CorElementType 値に対応します。  
  
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
 によって使用される値を提供します、 [IMetaDataValidate](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)モジュール (.obj ファイルと PE ファイル) の種類を指定するインターフェイス。  
  
 [COUNINITIEE 列挙型](../../../../docs/framework/unmanaged-api/metadata/couninitiee-enumeration.md)  
 使用される定数を指定します[CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)共通言語ランタイムを初期化するときにします。  
  
## <a name="related-sections"></a>関連項目  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
  
 [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [メタデータ構造体](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [メタデータ共用体](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
