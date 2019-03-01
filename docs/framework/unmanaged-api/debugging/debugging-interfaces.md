---
title: デバッグのインターフェイス
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d939063aaefb00d4db3de604df0dbd1b2175bf95
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981609"
---
# <a name="debugging-interfaces"></a>デバッグのインターフェイス
ここでは、共通言語ランタイム (CLR: Common Language Runtime) で実行するプログラムのデバッグを処理するアンマネージ インターフェイスについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ICLRDataEnumMemoryRegions インターフェイス](iclrdataenummemoryregions-interface.md)\
 呼び出し元が指定したメモリ範囲を列挙するメソッドを提供します。  
  
 [ICLRDataEnumMemoryRegionsCallback インターフェイス](iclrdataenummemoryregionscallback-interface.md)\
 メモリの指定された領域を列挙した結果の `EnumMemoryRegions` をデバッガーにレポートするコールバック メソッドを提供します。  
  
 [ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)\
 対象の CLR プロセスと対話するためのメソッドを提供します。  
  
 [ICLRDataTarget2 インターフェイス](iclrdatatarget2-interface.md)\
 データ アクセス サービス層で使用して対象プロセスの仮想メモリ領域を操作する、`ICLRDataTarget` のサブクラスです。  
  
 [ICLRDataTarget3 インターフェイス](iclrdatatarget3-interface.md)\
 サブクラス[ICLRDataTarget2](iclrdatatarget2-interface.md)例外情報へのアクセスを提供します。  
  
 [ICLRDebugging インターフェイス](iclrdebugging-interface.md)\
 デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。  
  
 [ICLRDebuggingLibraryProvider インターフェイス](iclrdebugginglibraryprovider-interface.md)\
 含まれています、 [ProvideLibrary メソッド](iclrdebugginglibraryprovider-providelibrary-method.md)メソッドで、ライブラリ プロバイダーの共通言語ランタイム バージョン固有デバッグ ライブラリを検索しに読み込む要求を許可するコールバック インターフェイスを取得します。  
  
 [ICLRMetadataLocator インターフェイス](iclrmetadatalocator-interface.md)\
 データ アクセス サービス層で使用して、対象プロセス内のアセンブリのメタデータを見つけるためのインターフェイスです。  
  
 [ICorDebug インターフェイス](icordebug-interface.md)\
 開発者が CLR 環境でアプリケーションをデバッグできるようにするメソッドを提供します。  
  
 [ICorDebugAppDomain インターフェイス](icordebugappdomain-interface.md)\
 アプリケーション ドメインをデバッグするためのメソッドを提供します。  
  
 [ICorDebugAppDomain2 インターフェイス](icordebugappdomain2-interface.md)\
 配列、ポインター、関数ポインター、および ByRef 型を使用するメソッドを提供します。 これは、`ICorDebugAppDomain` インターフェイスの機能を拡張するインターフェイスです。  
  
 [ICorDebugAppDomain3 インターフェイス](icordebugappdomain3-interface.md)\
 アプリケーション ドメインで [!INCLUDE[wrt](../../../../includes/wrt-md.md)] 型を操作するメソッドを提供します。 このインターフェイスは、`ICorDebugAppDomain` インターフェイスと `ICorDebugAppDomain2` インターフェイスを拡張します。  
  
 [ICorDebugAppDomain4 インターフェイス](icordebugappdomain4-interface.md)\
 論理的に拡張し、 [ICorDebugAppDomain](icordebugappdomain-interface.md)インターフェイスが COM 呼び出し可能ラッパーからマネージ オブジェクトを取得します。  
  
 [ICorDebugAppDomainEnum インターフェイス](icordebugappdomainenum-interface.md)\
 列挙体の次の位置から、指定した数の `ICorDebugAppDomain` の値を返すメソッドを提供します。  
  
 [ICorDebugArrayValue インターフェイス](icordebugarrayvalue-interface.md)\
 1 次元または多次元の配列を表す `ICorDebugHeapValue` のサブクラスです。  
  
 [ICorDebugAssembly インターフェイス](icordebugassembly-interface.md)\
 アセンブリを表します。  
  
 [ICorDebugAssembly2 インターフェイス](icordebugassembly2-interface.md)\
 アセンブリを表します。 これは、`ICorDebugAssembly` インターフェイスの機能を拡張するインターフェイスです。  
  
 [ICorDebugAssembly3 インターフェイス](icordebugassembly3-interface.md)\
 論理的に拡張し、 [ICorDebugAssembly](icordebugassembly-interface.md)コンテナー アセンブリとその格納されているアセンブリのサポートを提供するインターフェイス。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugAssemblyEnum インターフェイス](icordebugassemblyenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugAssembly` 配列を列挙します。  
  
 [ICorDebugBlockingObjectEnum インターフェイス](icordebugblockingobjectenum-interface.md)\
 一覧については、列挙子を提供します。 [CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体。  
  
 [ICorDebugBoxValue インターフェイス](icordebugboxvalue-interface.md)\
 ボックス化された値クラスのオブジェクトを表す `ICorDebugHeapValue` のサブクラス。  
  
 [ICorDebugBreakpoint インターフェイス](icordebugbreakpoint-interface.md)\
 関数のブレークポイント、または値のウォッチ ポイントを表します。  
  
 [ICorDebugBreakpointEnum インターフェイス](icordebugbreakpointenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugBreakpoint` 配列を列挙します。  
  
 [ICorDebugChain インターフェイス](icordebugchain-interface.md)\
 物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。  
  
 [ICorDebugChainEnum インターフェイス](icordebugchainenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugChain` 配列を列挙します。  
  
 [ICorDebugClass インターフェイス](icordebugclass-interface.md)\
 基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。 型がジェネリックの場合、`ICorDebugClass` はインスタンス化されないジェネリック型を表します。  
  
 [ICorDebugClass2 インターフェイス](icordebugclass2-interface.md)\
 ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。 このインターフェイスは、`ICorDebugClass` の機能を拡張します。  
  
 [ICorDebugCode インターフェイス](icordebugcode-interface1.md)\
 Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。  
  
 [ICorDebugCode2 インターフェイス](icordebugcode2-interface.md)\
 
  `ICorDebugCode` の機能を拡張するメソッドを提供します。  
  
 [ICorDebugCode3 インターフェイス](icordebugcode3-interface.md)\
 拡張メソッドを提供[ICorDebugCode](icordebugcode-interface1.md)と[ICorDebugCode2](icordebugcode2-interface.md)マネージ戻り値に関する情報を提供します。  
  
 [ICorDebugCode4 インターフェイス](icordebugcode4-interface.md)\
 ローカル変数と関数の引数を列挙するためにデバッガーをできるようにするメソッドを提供します。  
  
 [ICorDebugCodeEnum インターフェイス](icordebugcodeenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugCode` 配列を列挙します。  
  
 [ICorDebugComObjectValue のインターフェイス](icordebugcomobjectvalue-interface.md)\
 キャッシュされたインターフェイス オブジェクトを取得するメソッドを提供します。  
  
 [ICorDebugContext インターフェイス](icordebugcontext-interface.md)\
 コンテキストのオブジェクトを表します。 このインターフェイスはまだ実装されていません。  
  
 [ICorDebugController インターフェイス](icordebugcontroller-interface.md)\
 コードの実行コンテキストを制御できる <xref:System.Diagnostics.Process> または <xref:System.AppDomain> のスコープを表します。  
  
 [ICorDebugDataTarget インターフェイス](icordebugdatatarget-interface.md)\
 特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。  
  
 [ICorDebugDataTarget2 インターフェイス](icordebugdatatarget2-interface.md)\
 論理的に拡張し、 [ICorDebugDataTarget](icordebugdatatarget-interface.md)インターフェイス。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugDataTarget3 インターフェイス](icordebugdatatarget3-interface.md)\
 論理的に拡張し、 [ICorDebugDataTarget](icordebugdatatarget-interface.md)インターフェイスが読み込まれたモジュールに関する情報を提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugDebugEvent インターフェイス](icordebugdebugevent-interface.md)\
 すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugEditAndContinueErrorInfo インターフェイス](icordebugeditandcontinueerrorinfo-interface.md)\
 互換性のために残されています。 このインターフェイスは使用しないでください。  
  
 [ICorDebugEditAndContinueSnapshot インターフェイス](icordebugeditandcontinuesnapshot-interface.md)\
 互換性のために残されています。 このインターフェイスは使用しないでください。  
  
 [ICorDebugEnum インターフェイス](icordebugenum-interface1.md)\
 デバッグ中の列挙子の抽象基底インターフェイスとして機能します。  
  
 [ICorDebugErrorInfoEnum インターフェイス](icordebugerrorinfoenum-interface.md)\
 互換性のために残されています。 このインターフェイスは使用しないでください。  
  
 [ICorDebugEval インターフェイス](icordebugeval-interface.md)\
 デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。  
  
 [ICorDebugEval2 インターフェイス](icordebugeval2-interface.md)\
 ジェネリック型をサポートできるように `ICorDebugEval` を拡張します。  
  
 [ICorDebugExceptionDebugEvent インターフェイス](icordebugexceptiondebugevent-interface.md)\
 拡張、 [ICorDebugDebugEvent](icordebugdebugevent-interface.md)例外イベントをサポートするインターフェイス。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugExceptionObjectCallStackEnum インターフェイス](icordebugexceptionobjectcallstackenum-interface.md)\
 例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。  
  
 [ICorDebugExceptionObjectValue インターフェイス](icordebugexceptionobjectvalue-interface.md)\
 拡張、 [ICorDebugObjectValue](icordebugobjectvalue-interface.md)マネージ例外オブジェクトからスタック トレース情報を提供するインターフェイス。  
  
 [ICorDebugFrame インターフェイス](icordebugframe-interface.md)\
 現在のスタックのフレームを表します。  
  
 [ICorDebugFrameEnum インターフェイス](icordebugframeenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugFrame` 配列を列挙します。  
  
 [ICorDebugFunction インターフェイス](icordebugfunction-interface1.md)\
 マネージド関数またはマネージド メソッドを表します。  
  
 [ICorDebugFunction2 インターフェイス](icordebugfunction2-interface.md)\
 
  `ICorDebugFunction` を論理的に拡張して、"マイ コードのみ" ステップ実行によるデバッグをサポートします。  
  
 [ICorDebugFunction3 インターフェイス](icordebugfunction3-interface.md)\
 論理的に拡張し、 [ICorDebugFunction](icordebugfunction-interface1.md) ReJIT 要求からコードへのアクセスを提供するインターフェイス。  
  
 [ICorDebugFunctionBreakpoint インターフェイス](icordebugfunctionbreakpoint-interface.md)\
 関数内のブレークポイントをサポートするように `ICorDebugBreakpoint` を拡張します。  
  
 [ICorDebugGCReferenceEnum インターフェイス](icordebuggcreferenceenum-interface.md)\
 ガベージ コレクトされるオブジェクトの列挙子を提供します。  
  
 [ICorDebugGenericValue インターフェイス](icordebuggenericvalue-interface.md)\
 すべての値に適用する `ICorDebugValue` のサブクラスです。 このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。  
  
 [ICorDebugGuidToTypeEnum インターフェイス](icordebugguidtotypeenum-interface.md)\
 GUID およびその対応する `ICorDebugType` オブジェクトをマップするオブジェクトの列挙子を提供します。  
  
 [ICorDebugHandleValue インターフェイス](icordebughandlevalue-interface.md)\
 デバッガーが作成したガベージ コレクションのハンドルへの参照値を表す `ICorDebugReferenceValue` のサブクラスです。  
  
 [ICorDebugHeapEnum インターフェイス](icordebugheapenum-interface.md)\
 マネージド ヒープのオブジェクトの列挙子を提供します。  
  
 [ICorDebugHeapSegmentEnum インターフェイス](icordebugheapsegmentenum-interface.md)\
 マネージド ヒープのメモリ領域の列挙子を提供します。  
  
 [ICorDebugHeapValue インターフェイス](icordebugheapvalue-interface.md)\
 CLR ガベージ コレクターによって収集されたオブジェクトを表す `ICorDebugValue` のサブクラスです。  
  
 [ICorDebugHeapValue2 インターフェイス](icordebugheapvalue2-interface1.md)\
 ランタイム ハンドルのサポートを提供する `ICorDebugHeapValue` の拡張機能です。  
  
 [ICorDebugHeapValue3 インターフェイス](icordebugheapvalue3-interface.md)\
 オブジェクトのモニター ロック プロパティを公開します。  
  
 [ICorDebugILCode インターフェイス](icordebugilcode-interface.md)\
 中間言語 (IL) コードのセグメントを表します。  
  
 [ICorDebugILCode2 インターフェイス](icordebugilcode2-interface.md)\
 論理的に拡張し、 [ICorDebugILCode](icordebugilcode-interface.md)に元のメソッド IL オフセットを関数のローカル変数シグネチャのトークンを返すし、プロファイラーのインストルメント化された中間言語 (IL) をマップする方法を提供するインターフェイスオフセットします。  
  
 [ICorDebugILFrame インターフェイス](icordebugilframe-interface.md)\
 MSIL コードのスタック フレームを表します。  
  
 [ICorDebugILFrame2 インターフェイス](icordebugilframe2-interface.md)\
 
  `ICorDebugILFrame` の論理拡張機能です。  
  
 [ICorDebugILFrame3 インターフェイス](icordebugilframe3-interface.md)\
 関数の戻り値をカプセル化するメソッドを提供します。  
  
 [ICorDebugILFrame4 インターフェイス](icordebugilframe4-interface.md)\
 ローカル変数にアクセスできるようにするメソッドおよび中間言語 (IL) コードのスタック フレームのコードを提供します。 パラメーターは、プロファイラーの ReJIT インストルメンテーションに追加される変数およびコードへデバッガーがアクセスできるかどうかを指定します。  
  
 [ICorDebugInstanceFieldSymbol インターフェイス](icordebuginstancefieldsymbol-interface.md)\
 インスタンス フィールドのデバッグ シンボル情報を表します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugInternalFrame インターフェイス](icordebuginternalframe-interface.md)\
 デバッガーのフレーム種類を識別します。  
  
 [ICorDebugInternalFrame2 インターフェイス](icordebuginternalframe2-interface.md)\
 スタックのアドレスや位置などの内部フレームに関する情報を提供します[ICorDebugFrame](icordebugframe-interface.md)オブジェクト。  
  
 [ICorDebugLoadedModule インターフェイス](icordebugloadedmodule-interface.md)\
 読み込まれたモジュールについての情報を提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)\
 デバッガーのコールバックを処理するメソッドを提供します。  
  
 [ICorDebugManagedCallback2 インターフェイス](icordebugmanagedcallback2-interface.md)\
 デバッガーの例外処理およびマネージド デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。 `ICorDebugManagedCallback2` は、`ICorDebugManagedCallback` の論理拡張機能です。  
  
 [ICorDebugManagedCallback3 インターフェイス](icordebugmanagedcallback3-interface.md)\
 有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。  
  
 [ICorDebugMDA インターフェイス](icordebugmda-interface.md)\
 マネージド デバッグ アシスタント (MDA) メッセージを表します。  
  
 [ICorDebugMemoryBuffer インターフェイス](icordebugmemorybuffer-interface.md)\
 メモリ内のバッファーを表します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugMergedAssemblyRecord インターフェイス](icordebugmergedassemblyrecord-interface.md)\
 マージされたアセンブリに関する情報を提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugMetaDataLocator インターフェイス](icordebugmetadatalocator-interface.md)\
 デバッガーにメタデータ情報を提供します。  
  
 [ICorDebugModule インターフェイス](icordebugmodule-interface.md)\
 実行可能ファイルまたはダイナミック リンク ライブラリ (DLL: Dynamic-Link Library) のいずれかの CLR モジュールを表します。  
  
 [ICorDebugModule2 インターフェイス](icordebugmodule2-interface.md)\
 
  `ICorDebugModule` の論理的な拡張機能として動作します。  
  
 [ICorDebugModule3 インターフェイス](icordebugmodule3-interface.md)\
 動的モジュールのシンボル リーダーを作成します。  
  
 [ICorDebugModuleBreakpoint インターフェイス](icordebugmodulebreakpoint-interface.md)\
 特定のモジュールにアクセスできるように `ICorDebugBreakpoint` を拡張します。  
  
 [ICorDebugModuleDebugEvent インターフェイス](icordebugmoduledebugevent-interface.md)\
 拡張、 [ICorDebugDebugEvent](icordebugdebugevent-interface.md)モジュール レベルのイベントをサポートするインターフェイス。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugModuleEnum インターフェイス](icordebugmoduleenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugModule` 配列を列挙します。  
  
 [ICorDebugMutableDataTarget インターフェイス](icordebugmutabledatatarget-interface.md)\
 拡張、 [ICorDebugDataTarget](icordebugdatatarget-interface.md)変更可能なデータのターゲットをサポートするインターフェイス。  
  
 [ICorDebugNativeFrame インターフェイス](icordebugnativeframe-interface.md)\
 ネイティブ フレームで使用される `ICorDebugFrame` の特化された実装。  
  
 [ICorDebugNativeFrame2 インターフェイス](icordebugnativeframe2-interface.md)\
 子と親のフレームの関係をテストするメソッドを提供します。  
  
 [ICorDebugObjectEnum インターフェイス](icordebugobjectenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、オブジェクトの配列を相対仮想アドレス (RVA: Relative Virtual Address) で列挙します。  
  
 [ICorDebugObjectValue インターフェイス](icordebugobjectvalue-interface.md)\
 オブジェクトが含まれた値を表す `ICorDebugValue` のサブクラスです。  
  
 [ICorDebugObjectValue2 インターフェイス](icordebugobjectvalue2-interface.md)\
 継承およびオーバーライドをサポートするように `ICorDebugObjectValue` を拡張します。  
  
 [ICorDebugProcess インターフェイス](icordebugprocess-interface.md)\
 マネージド コードを実行しているプロセスを表します。  
  
 [ICorDebugProcess2 インターフェイス](icordebugprocess2-interface1.md)\
 
  `ICorDebugProcess` の論理拡張機能です。  
  
 [ICorDebugProcess3 インターフェイス](icordebugprocess3-interface.md)\
 カスタムのデバッガー通知を制御します。

 [ICorDebugProcess4 インターフェイス](icordebugprocess4-interface.md)\
 プロセス実行の制御外のサポートを提供します。
  
 [ICorDebugProcess5 インターフェイス](icordebugprocess5-interface.md)\
 拡張、 [ICorDebugProcess](icordebugprocess-interface.md)マネージ オブジェクトのガベージ コレクションに関する情報を提供し、デバッガーがアプリケーションからイメージを読み込むかどうかを判断する、マネージ ヒープへのアクセスをサポートするインターフェイスのローカルネイティブ イメージ キャッシュします。  
  
 [ICorDebugProcess6 インターフェイス](icordebugprocess6-interface.md)\
 論理的に拡張し、 [ICorDebugProcess](icordebugprocess-interface.md)ネイティブ例外デバッグ イベントや仮想モジュール分割でエンコードされたマネージ デバッグ イベントをデコードなどの機能を有効にするインターフェイス。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugProcess7 インターフェイス](icordebugprocess7-interface.md)\
 ターゲット プロセスでメモリ内のメタデータ更新を処理するようにデバッガーを構成するメソッドを提供します。  
  
 [ICorDebugProcess8 インターフェイス](icordebugprocess8-interface.md)\
 論理的に拡張し、 [ICorDebugProcess](icordebugprocess-interface.md)を有効にするまたはの特定の種類を無効にするインターフェイス[ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)例外コールバック。  
  
 [ICorDebugProcessEnum インターフェイス](icordebugprocessenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugProcess` 配列を列挙します。  
  
 [ICorDebugReferenceValue インターフェイス](icordebugreferencevalue-interface.md)\
 参照型をサポートする `ICorDebugValue` のサブクラス。  
  
 [ICorDebugRegisterSet インターフェイス](icordebugregisterset-interface.md)\
 現在コードを実行しているマシン上で使用できるレジスタ セットを表します。  
  
 [ICorDebugRegisterSet2 インターフェイス](icordebugregisterset2-interface.md)\
 64 を超えるレジスタを持つハードウェア プラットフォーム用に `ICorDebugRegisterSet` の機能を拡張します。  
  
 [ICorDebugRemote インターフェイス](icordebugremote-interface.md)\
 リモート ターゲット プロセスに対してマネージド デバッガーを起動または接続する機能を提供します。  
  
 [ICorDebugRemoteTarget インターフェイス](icordebugremotetarget-interface.md)\
 開発者が CLR 環境で Silverlight ベース アプリケーションをデバッグできるようにするメソッドを提供します。  
  
 [ICorDebugRuntimeUnwindableFrame インターフェイス](icordebugruntimeunwindableframe-interface.md)\
 共通言語ランタイム (CLR: Common Language Runtime) でフレームをアンワインドする必要のあるアンマネージ メソッドに対してサポートを提供します。  
  
 [ICorDebugStackWalk インターフェイス](icordebugstackwalk-interface.md)\
 スレッドのスタック上のマネージド メソッド (フレーム) を取得するメソッドを提供します。  
  
 [ICorDebugStaticFieldSymbol インターフェイス](icordebugstaticfieldsymbol-interface.md)\
 静的フィールドのデバッグ シンボル情報を表します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugStepper インターフェイス](icordebugstepper-interface.md)\
 デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。  
  
 [ICorDebugStepper2 インターフェイス](icordebugstepper2-interface1.md)\
 マイ コードのみ (JMC: Just My Code) デバッグのサポートを提供します。  
  
 [ICorDebugStepperEnum インターフェイス](icordebugstepperenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugStepper` 配列を列挙します。  
  
 [ICorDebugStringValue インターフェイス](icordebugstringvalue-interface.md)\
 文字列値に適用する `ICorDebugHeapValue` のサブクラスです。  
  
 [ICorDebugSymbolProvider インターフェイス](icordebugsymbolprovider-interface.md)\
 デバッグ シンボル情報を取得するために使用できるメソッドを提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugSymbolProvider2 インターフェイス](icordebugsymbolprovider2-interface.md)\
 論理的に拡張し、 [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)追加のデバッグ シンボル情報を取得するインターフェイス。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugThread インターフェイス](icordebugthread-interface.md)\
 プロセス内のスレッドを表します。 
  `ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。  
  
 [ICorDebugThread2 インターフェイス](icordebugthread2-interface.md)\
 
  `ICorDebugThread` の論理的な拡張機能として動作します。  
  
 [ICorDebugThread3 インターフェイス](icordebugthread3-interface.md)\
 エントリ ポイントを提供します、 [ICorDebugStackWalk](icordebugstackwalk-interface.md)と対応するインターフェイス。  
  
 [ICorDebugThread4 インターフェイス](icordebugthread4-interface.md)\
 スレッドのブロック情報を提供します。  
  
 [ICorDebugThreadEnum インターフェイス](icordebugthreadenum-interface1.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugThread` 配列を列挙します。  
  
 [ICorDebugType インターフェイス](icordebugtype-interface.md)\
 基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。 型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。  
  
 [ICorDebugType2 インターフェイス](icordebugtype2-interface.md)\
 拡張、 [ICorDebugType](icordebugtype-interface.md)基本型または複合 (ユーザー定義) の型の型の識別子を取得するインターフェイス。  
  
 [ICorDebugTypeEnum インターフェイス](icordebugtypeenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugType` 配列を列挙します。  
  
 [ICorDebugUnmanagedCallback インターフェイス](icordebugunmanagedcallback-interface.md)\
 CLR に直接関連していないネイティブ イベントについて通知します。  
  
 [ICorDebugValue](icordebugvalue-interface.md)\
 デバッグ中のプロセス内の読み取り値または書き込み値を表します。  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 
  `ICorDebugValue` をサポートできるように `ICorDebugType` を拡張します。  
  
 [ICorDebugValue3 インターフェイス](icordebugvalue3-interface.md)\
 2 GB を超える配列のサポートを提供する"ICorDebugValue"と"ICorDebugValue2"インターフェイスを拡張します。  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 特定の値にアクセスできるように `ICorDebugBreakpoint` を拡張します。  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 
  `ICorDebugEnum` メソッドを実装し、`ICorDebugValue` 配列を列挙します。  
  
 [ICorDebugVariableHome インターフェイス](icordebugvariablehome-interface.md)\
 ローカル変数または関数の引数を表します。  
  
 [ICorDebugVariableHomeEnum インターフェイス](icordebugvariablehomeenum-interface.md)\
 ローカル変数と関数の引数、列挙子を提供します。  
  
 [ICorDebugVariableSymbol インターフェイス](icordebugvariablesymbol-interface.md)\
 変数のデバッグ シンボル情報を取得します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugVirtualUnwinder インターフェイス](icordebugvirtualunwinder-interface.md)\
 スタック アンワインドを支援するメソッドを提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorPublish インターフェイス](icorpublish-interface.md)\
 発行プロセスの汎用インターフェイスとして機能します。  
  
 [ICorPublishAppDomain インターフェイス](icorpublishappdomain-interface.md)\
 アプリケーション ドメインの情報を表し、提供します。  
  
 [ICorPublishAppDomainEnum インターフェイス](icorpublishappdomainenum-interface.md)\
 現在プロセス内に存在する `ICorPublishAppDomain` オブジェクトのコレクションを走査するメソッドを提供します。  
  
 [ICorPublishEnum インターフェイス](icorpublishenum-interface.md)\
 発行する列挙子の抽象ベースとして機能します。  
  
 [ICorPublishProcess インターフェイス](icorpublishprocess-interface.md)\
 プロセスの情報にアクセスするメソッドを適用します。  
  
 [ICorPublishProcessEnum インターフェイス](icorpublishprocessenum-interface.md)\
 
  `ICorPublishProcess` オブジェクトのコレクションを走査するメソッドを提供します。  

 [ISOSDacInterface インターフェイス](isosdacinterface-interface.md)\
 データにアクセスするヘルパー メソッドを提供します。`SOS`します。

 [IXCLRDataMethodDefinition インターフェイス](ixclrdatamethoddefinition-interface.md)\
 メソッドの定義に関する情報を照会するためのメソッドを提供します。
 
 [IXCLRDataMethodInstance インターフェイス](ixclrdatamethodinstance-interface.md)\
 メソッド インスタンスの情報を照会するためのメソッドを提供します。
 
 [IXCLRDataModule インターフェイス](ixclrdatamodule-interface.md)\
 読み込まれたモジュールに関する情報を照会するためのメソッドを提供します。
 
 [IXCLRDataProcess インターフェイス](ixclrdataprocess-interface.md)\
 プロセスの情報を照会するためのメソッドを提供します。
  
## <a name="related-sections"></a>関連項目  
 [デバッグ コクラス](debugging-coclasses.md)\
 [デバッグ グローバル静的関数](debugging-global-static-functions.md)\
 [列挙体のデバッグ](debugging-enumerations.md)\
 [デバッグ構造体](debugging-structures.md)\
