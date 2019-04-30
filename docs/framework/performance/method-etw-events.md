---
title: メソッド ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7969c0a3f5f828f1a1c0d4f33b82881130c6e15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949254"
---
# <a name="method-etw-events"></a>メソッド ETW イベント

<a name="top"></a> これらのイベントは、メソッド固有の情報を収集します。 これらのイベントのペイロードは、シンボルの解決に必要です。 さらに、これらのイベントは、メソッドが呼び出された回数などの有用な情報を提供します。

すべてのメソッド イベントのレベルは「情報提供 (4)」です。 すべてのメソッド詳細イベントのレベルは「詳細 (5)」です。

すべてのメソッド イベントは、ランタイム プロバイダーのもとでは `JITKeyword` (0x10) キーワードまたは `NGenKeyword` (0x20) キーワードが発生させ、ランダウン プロバイダーのもとでは `JitRundownKeyword` (0x10) または `NGENRundownKeyword` (0x20) が発生させます。

CLR メソッド イベントは、さらに次のように細分化されます。

- [CLR メソッド イベント](#clr_method_events)

- [CLR メソッド マーカー イベント](#clr_method_marker_events)

- [CLR メソッド詳細イベント](#clr_method_verbose_events)

- [MethodJittingStarted イベント](#methodjittingstarted_event)

<a name="clr_method_events"></a>

## <a name="clr-method-events"></a>CLR メソッド イベント

次の表に、キーワードとレベルを示します。 (詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) ランタイム プロバイダー|情報提供 (4)|
|`NGenKeyword` (0x20) ランタイム プロバイダー|情報提供 (4)|
|`JitRundownKeyword` (0x10) ランダウン プロバイダー|情報提供 (4)|
|`NGENRundownKeyword` (0x20) ランダウン プロバイダー|情報提供 (4)|

次の表に、イベント情報を示します。

|イベント|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|136|メソッドが Just-In-Time 読み込み (JIT 読み込み) される時点、または NGEN イメージが読み込まれる時点で発生します。 動的メソッドとジェネリック メソッドは、メソッドの読み込みにこのバージョンを使用しません。 JIT ヘルパーがこのバージョンを使用することはありません。|
|`MethodUnLoad_V1`|137|モジュールがアンロードされるとき、またはアプリケーション ドメインが破棄されるときに発生します。 動的メソッドがメソッドのアンロードにこのバージョンを使用することはありません。|
|`MethodDCStart_V1`|137|開始ランダウン中にメソッドを列挙します。|
|`MethodDCEnd_V1`|138|終了ランダウン中にメソッドを列挙します。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|メソッドの一意の識別子。 JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。|
|ModuleID|win:UInt64|このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。|
|MethodStartAddress|win:UInt64|メソッドの開始アドレス。|
|MethodSize|win:UInt32|メソッドのサイズ。|
|MethodToken|win:UInt32|動的メソッドおよび JIT ヘルパーの場合は 0。|
|MethodFlags|win:UInt32|0x1:動的メソッド。<br /><br /> 0x2:ジェネリック メソッド。<br /><br /> 0x4:コードの JIT コンパイルされたメソッド (それ以外の場合の NGEN ネイティブ イメージ コード)。<br /><br /> 0x8:ヘルパー メソッドです。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|

[ページのトップへ](#top)

<a name="clr_method_marker_events"></a>

## <a name="clr-method-marker-events"></a>CLR メソッド マーカー イベント

これらのイベントはランダウン プロバイダーのもとでしか発生しません。 これらは、開始ランダウンまたは終了ランダウン中にメソッド列挙体の終わりを示します。 (つまり、 `NGENRundownKeyword`、 `JitRundownKeyword`、 `LoaderRundownKeyword`、または `AppDomainResourceManagementRundownKeyword` のキーワードが有効な場合に発生します。)

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`AppDomainResourceManagementRundownKeyword` (0x800) ランダウン プロバイダー|情報提供 (4)|
|`JitRundownKeyword` (0x10) ランダウン プロバイダー|情報提供 (4)|
|`NGENRundownKeyword` (0x20) ランダウン プロバイダー|情報提供 (4)|

次の表に、イベント情報を示します。

|イベント|イベント ID|説明|
|-----------|--------------|----------------|
|`DCStartInit_V1`|147|開始ランダウン中に列挙体の始まりの前に送信されます。|
|`DCStartComplete_V1`|145|開始ランダウン中に列挙体の終わりに送信されます。|
|`DCEndInit_V1`|148|終了ランダウン中に列挙体の始まりの前に送信されます。|
|`DCEndComplete_V1`|146|終了ランダウン中に列挙体の終わりに送信されます。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|

[ページのトップへ](#top)

<a name="clr_method_verbose_events"></a>

## <a name="clr-method-verbose-events"></a>CLR メソッド詳細イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) ランタイム プロバイダー|詳細 (5)|
|`NGenKeyword` (0x20) ランタイム プロバイダー|詳細 (5)|
|`JitRundownKeyword` (0x10) ランダウン プロバイダー|詳細 (5)|
|`NGENRundownKeyword` (0x20) ランダウン プロバイダー|詳細 (5)|

次の表に、イベント情報を示します。

|イベント|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|メソッドが JIT 読み込みされるとき、または NGEN イメージが読み込まれるときに発生します。 動的メソッドとジェネリック メソッドは、メソッドの読み込みに常にこのバージョンを使用します。 JIT ヘルパーは常にこのバージョンを使用します。|
|`MethodUnLoadVerbose_V1`|144|動的メソッドが破棄されるとき、またはモジュールがアンロードされるとき、あるいはアプリケーション ドメインが破棄されるときに発生します。 動的メソッドは、メソッドのアンロードに常にこのバージョンを使用します。|
|`MethodDCStartVerbose_V1`|141|開始ランダウン中にメソッドを列挙します。|
|`MethodDCEndVerbose_V1`|142|終了ランダウン中にメソッドを列挙します。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|メソッドの一意の識別子。 JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。|
|ModuleID|win:UInt64|このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。|
|MethodStartAddress|win:UInt64|開始アドレス。|
|MethodSize|win:UInt32|メソッドの長さ。|
|MethodToken|win:UInt32|動的メソッドおよび JIT ヘルパーの場合は 0。|
|MethodFlags|win:UInt32|0x1:動的メソッド。<br /><br /> 0x2:ジェネリック メソッド。<br /><br /> 0x4:(それ以外の場合、NGen.exe によって生成された) メソッドを JIT コンパイル<br /><br /> 0x8:ヘルパー メソッドです。|
|MethodNameSpace|win:UnicodeString|メソッドに関連付けられた完全な名前空間名。|
|MethodName|win:UnicodeString|メソッドに関連付けられた完全クラス名。|
|MethodSignature|win:UnicodeString|メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|

[ページのトップへ](#top)

<a name="methodjittingstarted_event"></a>

## <a name="methodjittingstarted-event"></a>MethodJittingStarted イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) ランタイム プロバイダー|詳細 (5)|
|`NGenKeyword` (0x20) ランタイム プロバイダー|詳細 (5)|
|`JitRundownKeyword` (0x10) ランダウン プロバイダー|詳細 (5)|
|`NGENRundownKeyword` (0x20) ランダウン プロバイダー|詳細 (5)|

次の表に、イベント情報を示します。

|イベント|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodJittingStarted`|145|メソッドが JIT コンパイルされているときに発生します。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|メソッドの一意の識別子。|
|ModuleID|win:UInt64|このメソッドが属するモジュールの識別子。|
|MethodToken|win:UInt32|動的メソッドおよび JIT ヘルパーの場合は 0。|
|MethodILSize|win:UInt32|JIT コンパイルされているメソッドの Microsoft intermediate language (MSIL) のサイズ。|
|MethodNameSpace|win:UnicodeString|メソッドに関連付けられた完全クラス名。|
|MethodName|win:UnicodeString|メソッドの名前です。|
|MethodSignature|win:UnicodeString|メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="see-also"></a>関連項目

- [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)
