---
title: 要素をオーバーライドします。
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 95ae438e9fb52cc584d18a981bffb66147eb4a77
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242817"
---
# <a name="appcontextswitchoverrides-element"></a>\<要素>オーバーライドします。

<xref:System.AppContext> クラスで使用される、新機能に対するオプトアウト メカニズムを指定するスイッチを 1 つまたは複数定義します。

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>をオーバーライドします。**

## <a name="syntax"></a>構文

```xml
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />
```

## <a name="attributes-and-elements"></a>属性および要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`value`|必須の属性です。<br /><br /> 1 つ以上のスイッチ名と、関連するブール値を定義します。|

### <a name="value-attribute"></a>値 属性

|[値]|説明|
|-----------|-----------------|
|"名前=値"|定義済みのスイッチ名とその値 (`true`または`false`) を指定します。 複数のスイッチの名前と値のペアは、セミコロン (";") で区切られます。 .NET Framework でサポートされている定義済みのスイッチ名の一覧については、「解説」を参照してください。|

### <a name="child-elements"></a>子要素
 なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|

## <a name="remarks"></a>解説
 .NET Framework 4.6 以降では`<AppContextSwitchOverrides>`、構成ファイル内の要素を使用すると、API の呼び出し元は、アプリが新しい機能を利用できるか、または以前のバージョンのライブラリとの互換性を維持できるかどうかを判断できます。 たとえば、API の動作がライブラリの 2 つのバージョン間で変更された場合`<AppContextSwitchOverrides>`、要素は、その API の呼び出し元が、新しい機能をサポートするライブラリのバージョンで新しい動作をオプトアウトすることを許可します。 .NET Framework で API を呼び出`<AppContextSwitchOverrides>`すアプリの場合、この要素は、以前のバージョンの .NET Framework を対象とするアプリを含む .NET Framework バージョンでアプリが実行されている場合に、新しい機能を選択することを呼び出し元に許可することもできます。

 要素`value`の`<AppContextSwitchOverrides>`属性は、1 つ以上のセミコロン区切りの名前と値のペアで構成される単一の文字列で構成されます。  各名前は互換性スイッチを識別し、対応する値は、スイッチが`true`設定`false`されているかどうかを示すブール値 ( または ) です。 既定では、スイッチは、`false`ライブラリは、新しい機能を提供します。 スイッチが設定されている場合のみ、以前の機能を提供します (つまり、その`true`値は です)。 これにより、ライブラリは既存の API に新しい動作を提供し、以前の動作に依存する呼び出し元は新しい機能をオプトアウトできます。

 .NET Framework では、次のスイッチがサポートされています。

|スイッチ名|説明|導入|
|-----------------|-----------------|----------------|
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Windows プレゼンテーションファンデーションがコントロール レイアウトに従来のアルゴリズムを使用するかどうかを制御します。 詳細については、「[軽減策: WPF レイアウト](../../../migration-guide/mitigation-wpf-layout.md)」を参照してください。|.NET Framework 4.6|
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|パッケージのパーツに署名するために使用される既定のアルゴリズムが SHA1 または SHA256 かどうかを制御します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|に`false`設定すると、FIPS が有効になっているときに、Visual Studio で XAML ベースのワークフロー プロジェクトをデバッグできます。 これがなければ、System.Activities<xref:System.NullReferenceException>アセンブリ内のメソッドの呼び出しで a がスローされます。|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|デバッガーのワークフロー インスタンスのチェックサムで MD5 または SHA1 を使用するかどうかを制御します。 | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|ワークフロー チェックサム ハッシュで .NET Framework 4.7 ( ) の既定として`true`導入された SHA1 アルゴリズムを使用するかどうか、または .NET Framework 4.8 (`false`) で既定として導入された既定の SHA256 アルゴリズムを使用するかどうかを制御します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|ポータブル PDB を使用する場合にスタック トレースを取得するかどうかを制御します。 `false`ソース ファイルと行の情報を含める。それ以外`true`の場合は、 .|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|オブジェクトに<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType>PNG フレームがある場合に、<xref:System.Drawing.Icon>メソッドが例外をスローするかどうかを制御します。 詳細については、「[軽減策: Icon オブジェクトの PNG フレーム](../../../migration-guide/mitigation-png-frames-in-icon-objects.md)」を参照してください。|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|メソッドによって<xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType>コレクションに追加されたときにオブジェクトが適切に破棄されるかどうかを判断<xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>します。 `true`従来の動作を維持するため。`false`すべてのプライベート フォント オブジェクトを破棄します。 |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|のパフォーマンス<xref:System.Windows.Forms.PrintPreviewDialog>がネットワーク プリンタに最適化されているかどうかを制御します。 詳細については、「[コントロールの印刷プレビューダイアログの概要](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md)」を参照してください。|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|日本の暦年の年の範囲チェックを実施するかどうかを制御します。 `true`年範囲チェックを実施し`false`、それらを無効にします (既定の動作)。 詳細については、「[カレンダーの操作](../../../../standard/datetime/working-with-calendars.md)」を参照してください。|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|解析操作で、日本暦の最初の年として"1"のみを認識するかどうかを制御します。 `true`"1" のみを認識する。`false` 「1」またはギャネン(デフォルトの動作)のいずれかを認識します。 詳細については、「[カレンダーの操作](../../../../standard/datetime/working-with-calendars.md)」を参照してください。|.NET Framework 4.6|
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|書式設定操作で、日本暦の最初の年を "1" または "Gannen" のどちらで表すかを制御します。 `true`時代の最初の年を「1」としてフォーマットする。`false`をクリックして、ギャネン (デフォルトの動作) としてフォーマットします。 詳細については、「[カレンダーの操作](../../../../standard/datetime/working-with-calendars.md)」を参照してください。|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|非同期操作が呼び出し元スレッドのコンテキストからフローしないかどうかを制御します。 詳細については、「[タスク間の現在のカルチャと現在の UI カルチャのフロー](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks)」を参照してください。|.NET Framework 4.6|
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|メソッドが要求<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType>の種類と最後の DNS エントリのみを照合するかどうかを制御します。 詳細については、「[軽減策: X509CertificateClaimSet.FindClaims メソッド](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)」を参照してください。|.NET Framework 4.6.1|
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|変更可能なオブジェクトを返すことを許可するかどうかを制御します。|.NET Framework 4.6|
|`Switch.System.IO.BlockLongPaths`|パスが 260 文字より`MAX_PATH`長い場合に<xref:System.IO.PathTooLongException>. 詳細については、「ロング[パスのサポート](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support)」を参照してください。|.NET Framework 4.6.2|
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|クラスによる圧縮解除にネイティブ OS ルーチンを使用するかどうかを<xref:System.IO.Compression.DeflateStream>制御します。 `false`ネイティブ API を使用する。`true`をクリックして<xref:System.IO.Compression.DeflateStream>実装を使用します。|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|プロパティのパス区切り記号\\として、スラッシュ ("/") ではなく円記号 ("" ) を使用します。 <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> 詳細については、「[軽減策: ZipArchiveEntry.FullName パス区切り記号](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)」を参照してください。|.NET Framework 4.6.1|
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|ストリームで<xref:System.IO.Ports.SerialPort>作成されたバックグラウンド スレッドでスローされるオペレーティング システムの例外がプロセスを終了するかどうかを制御します。|.NET Framework 4.7.1|
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|レガシ パスの正規化を使用し、URI パスを<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> and メソッドでサポートするかどうかを制御します。 詳細については、「[軽減策: パスの正規化](../../../migration-guide/mitigation-path-normalization.md)と[軽減策: パス コロンのチェック](../../../migration-guide/mitigation-path-colon-checks.md)」を参照してください。|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|等値のテストで、あるオブジェクトのプロパティ<xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType>と 2 番目の<xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType>オブジェクトのプロパティを比較するかどうかを制御します。 詳細については、「 [MemberDescriptor.Equals の不適切な実装](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals)」を参照してください。|.NET Framework 4.6.2|
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|証明書拡張キー使用法 (EKU) オブジェクト識別子 (OID) の検証を無効にします。 EKU (拡張キー使用法) 拡張は、キーを使用するアプリケーションを示すオブジェクト識別子 (OID) の集まりです。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|SCH_SEND_AUX_RECORDの使用を無効にすることにより、SSL/TLS (BEAST) に対する TLS1.0 ブラウザーエクスプロイトの軽減を無効にします。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|および<xref:System.Net.Security.SslStream?displayProperty=nameWithType>クラス<xref:System.Net.ServicePointManager?displayProperty=nameWithType>が SSL 3.0 プロトコルを使用できるかどうかを制御します。 詳細については、「[軽減策: TLS プロトコル](../../../migration-guide/mitigation-tls-protocols.md)」を参照してください。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|デフォルトの Tls12、Tls11、Tls に戻すシステムデフォルト TLS バージョンを無効にします。|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|SSL ストリーム TLS サーバー側アラートを無効にします。|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|COM 相互運用イベントの ByRef SafeArray パラメーターをネイティブ コード`false`( ) にマーシャリングして元に戻す`true`かどうか、またはネイティブ コードへのマーシャリングが無効になっているか ( ) を制御します。|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |ECMAScript V6 標準と V8[標準に基](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer)づいて、一部の制御文字をシリアル化するかどうかを制御します。 詳細については、「[軽減策: DataContractJsonSerializer での制御文字のシリアル化](../../../migration-guide/mitigation-serialization-control-characters.md)」を参照してください。| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|複数の調整<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>をサポートするか、1 つのタイム ゾーンに対して 1 つの調整のみをサポートするかを制御します。 の`true`場合は、型<xref:System.TimeZoneInfo>を使用して日付と時刻のデータをシリアル化および逆シリアル化します。それ以外の場合は<xref:System.TimeZone>、複数の調整規則をサポートしない型を使用します。|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|オブジェクトの<xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType>シリアル化と逆シリアル化の際に、より大きな配列サイズを使用するかどうかを制御します。 などの型によって大`true`きなオブジェクト グラフのシリアル化と逆シリアル化のパフォーマンスを向上させるには、この<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>スイッチを に設定します。 |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|コンストラクターが、<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29>既存のオブジェクト参照を使用して<xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType>新しいオブジェクトのプロパティを設定するかどうかを制御します。 詳細については、「[軽減策: ClaimsIdentity コンストラクター](../../../migration-guide/retargeting/4.6.1-4.6.2.md)」を参照してください。|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|<xref:System.Security.Cryptography.AesCryptoServiceProvider>復号化を再利用する試みが<xref:System.Security.Cryptography.CryptographicException>. 詳細については、「 [AesCryptoServiceProvider 復号化機能は再利用可能な変換を提供する」を](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform)参照してください。|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|[プロパティの](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle)値がウィンドウ ハンドルのメモリ位置を表す[IntPtr](xref:System.IntPtr)であるか、ウィンドウ ハンドル (HWND) であるかどうかを制御します。 詳細については、「[Mitigation: CspParameters.ParentWindowHandle Expects an HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value)」 (軽減策: CspParameters.ParentWindowHandle で HWND を受け取る) を参照してください。 |.NET Framework 4.7|
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|FIPS モードでのマネージ暗号化クラスの使用が<xref:System.Security.Cryptography.CryptographicException>、 )`true`をスローするか、 ( ) システム`false`ライブラリの実装に依存するかを制御します。|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|一部の SignedCMS 操作のデフォルトが SHA1 または SHA256 かどうかを決定します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|<xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType>オペレーティング システム ( ) でサポートされているすべての名前付き曲線`false`をメソッドが正しく処理するか、または従来の動作に戻すかを制御します。|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|一部の SignedXML 操作のデフォルトが SHA1 または SHA256 かどうかを決定します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|セキュリティ モード`TransportWithMessageCredential`で、署名のない "to" ヘッダーを持つメッセージを許可するかどうかを決定します。 これはオプトイン スイッチです。 詳細については、「 [.NET Framework 4.6.1 のランタイムの変更](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf)」を参照してください。|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|コンストラクターが、<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>要素の 1<xref:System.ArgumentException>つが`null`の場合にをスローするかどうかを制御します。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|CSG キーストレージプロバイダで X509 証明書を使用しようとした場合に例外がスローされるかどうかを判断します。 詳細については、「 [WCF トランスポート セキュリティは CNG を使用して格納された証明書をサポートする](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng)」を参照してください。|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|HTTP トランスポートを自己ホスト型サービスで使用する場合、この値を設定`true`すると、WCF は要求の応答`Connection: close`ヘッダーにヘッダーを追加するアプリケーションを無視します。 この値を設定`false`して、応答`Connection: close`ヘッダーにヘッダーを追加できるようにし、応答が送信された後に要求ソケットを閉じます。|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|再入可能なサービスのインスタンスを一度に 1 つの実行スレッドに制限した結果生じるデッドロックを処理します。|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|と共`Switch.System.Net.DontEnableSchUseStrongCrypto`に、WCF メッセージ セキュリティで TLS 1.1 と TLS 1.2 を使用するかどうかを決定します。|.NET Framework 4.7 |
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|値を`false`設定すると、オペレーティング システムがプロトコルを選択できるように既定の構成が設定されます。 値を指定`true`すると、デフォルトは使用可能な最高のプロトコルに設定されます。 (以前のフレームワーク バージョンのサービス ブランチでも利用可能)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|WCF の MSMQ メッセージの既定のメッセージ署名アルゴリズムが SHA1 または SHA256 かどうかを決定します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|WCF が SHA1 ハッシュを使用するか、SHA256 ハッシュを使用して名前付きパイプのランダムな名前を生成するかを制御します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|例外メッセージが null の場合に[Null 参照例外](xref:System.NullReferenceException)をスローするかどうかを制御します。|.NET Framework 4.7|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|サービスの起動時にスローされた例外をメソッドの呼び出し元に<xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>伝達するかどうかを制御します。|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|インスタンスが<xref:System.Threading.Timer>大規模な環境でパフォーマンスの向上を利用するかどうかを制御します。 の`true`場合、パフォーマンスの向上は有効です。(`false`デフォルト値)の場合、無効になります。|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|デコードされた可能性のあるパーセントエンコード文字が、一貫してエンコードされたままになっているかどうかを判断します。 の`true`場合、デコードされます。それ以外`false`の場合は、 .|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|URI での単一コード双方向文字の処理を決定します。 `true`URIからそれらを取り除くために;`false`を使用して、それらを保持し、パーセントエンコードします。|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |列に領域`true`\*を割り当てる場合に、古いアルゴリズム (`false`) または新しいアルゴリズム ( ) を適用するかどうかを決定します。 詳細については、「[Mitigation: Grid Control's Space Allocation to Star-columns](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns)」 (軽減策: グリッド コントロールの *-column へのディスク領域の割り当て) を参照してください。 |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|選択した変更イベントを発生させる前に、セレクターまたはタブ コントロールが常に選択した値プロパティの値を更新するかどうかを制御します。|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|非装飾ベースの選択レンダリングを、<xref:System.Windows.Controls.TextBox>コントロール<xref:System.Windows.Controls.PasswordBox>で遮蔽テキスト ( ) を防ぐか、または`false`テキストを装飾レイヤー ( )`true`でのみレンダリングするかを決定します。|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|カスタム IList インデクサーがクラスによって`true`正しく使用されない`false`( <xref:System.Windows.Data.Binding?displayProperty=nameWithType> ) または正しく使用されるかどうかを制御します。|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|DPI の変更がシステム単位 (値 ) で`false`発生するか (値は ) で`true`発生するか、モニタ単位 (値は ) にするかを決定します。|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|WPF がモニタごとの対応モードで実行されている<xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType>場合のコントロールのサイズ変更の改善を無効 ()`true`または有効`false`( ) にするかどうかを制御します。|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|コントロール テキストが存在する場合に、<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>開発者が特別にアクションを処理する必要があるかどうかを判断します。 `true`アクションを処理<xref:System.Windows.Forms.DomainUpDown.UpButton>する。`false`と<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>アクションが正しく同期されるようにします。|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|メソッドが呼び出されたときに例外をスローすることなく<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>、カスタム実装がメッセージを安全にフィルター処理できるようにする<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>コードをオプトアウトします。 詳細については、[「軽減策: カスタムの IMessageFilter.PreFilterMessage 実装」](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)を参照してください。|.NET Framework 4.6.1|
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|入れ子<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>になった<xref:System.Windows.Forms.ToolStripMenuItem>コントロールからユーザーがメニューを開いたときに、プロパティがソース コントロールを返すかどうかを判断します。 `true`を返`null`すために、従来の動作を返します。`false`をクリックしてソース管理を返します。|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|ツールヒントの起動のサポートを無効`true`()`false`または有効 ( ) にするかどうかを制御します。 ツールヒントの呼び出しのサポートを有効`Switch.UseLegacyAccessibilityFeatures`にするには`Switch.UseLegacyAccessibilityFeatures.2`、`Switch.UseLegacyAccessibilityFeatures.3`によって定義された従来のユーザー`false`補助機能も必要です ( に設定 ) 。|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|WPF アプリケーションで`WM_POINTER`オプションのタッチ/スタイラス スタックが有効かどうかを判断します。 詳細については、「[緩和策: ポインター ベースのタッチとスタイラスのサポート](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)」を参照してください。|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|チェックサムに使用されるデフォルトのハッシュアルゴリズムが SHA256 (`false`) または`true`SHA1 ( ) かどうかを判別します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|例外の原因をより具体的に示す例外の代わりに、従来の[NullReferenceException](xref:System.NullReferenceException)がスローされるかどうかを[制御します](xref:System.IO.FileNotFoundException)(たとえば、[例外](xref:System.IO.DirectoryNotFoundException)の原因を示します。 これは、[処理](xref:System.NullReferenceException)に依存するコードで使用することを目的としています。 | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|ワークフロー プロジェクト ビルドの XOML ファイルのチェックサム ハッシュで MD5`true`アルゴリズム ( ) を使用するか、.NET Framework 4.8 で既定として導入された SHA256 アルゴリズムを使用するかを制御します。<br>MD5 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|SqlTrackingService によるチェックサム ハッシュでキャッシュされた文字列に MD5`true`アルゴリズム ( ) を使用するか、.NET Framework 4.8 で既定として導入された SHA256 アルゴリズムを使用するかを制御します。<br>MD5 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|ワークフロー ランタイムによるチェックサム ハッシュでキャッシュされたワークフロー定義に MD5 アルゴリズム (`true`) を使用するか、.NET Framework 4.8 で既定として導入された SHA256 アルゴリズムを使用するかを制御します。<br>MD5 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|NET Framework 4.7.1 以降で利用可能なユーザー補助機能を有効にするか無効にするかを制御します。 | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|.NET Framework 4.7.2 で使用できるユーザー補助機能`false`を有効 () または無効 ( )`true`にするかどうかを制御します。 の`true`場合`Switch.UseLegacyAccessibilityFeatures`は、.NET Framework 4.7.1 のユーザー補助機能も有効にする必要があります`true`。|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|.NET Framework 4.8 で導入されたユーザー補助機能`false`を有効 () にするか 、 を無効にするかを制御します 。`true` の`true`場合`Switch.UseLegacyAccessibilityFeatures`は`Switch.UseLegacyAccessibilityFeatures.2`、 と`true`を指定する必要があります。|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|ユーザーが WPF コントロール ( ) の上にマウス カーソルを置`true`いたときにツールヒントを表示するか、キーボード フォーカスとキーボード ショートカット キー`false`(既定の動作) の両方にツールヒントを表示するかを制御します。 NET Framework 4.8 で実行されているが、以前のバージョンの .NET Framework を対象とするアプリケーションの場合、`Switch.UseLegacyAccessibilityFeatures`キーボード`Switch.UseLegacyAccessibilityFeatures.2`フォーカス`Switch.UseLegacyAccessibilityFeatures.3`とショートカット キー`false`の両方のサポートを有効にするには、 、およびすべて に設定する必要があります。|.NET Framework 4.8|
|`Switch.System.Xml.`<br />`IgnoreEmptyKeySequences`|複合キーの空のキー シーケンスを XSD スキーマ検証によって無視するかどうかを制御します。 詳細については、「[緩和策: XML スキーマ検証](../../../migration-guide/mitigation-xml-schema-validation.md)」を参照してください。|.NET Framework 4.6|

> [!NOTE]
> アプリケーション構成ファイルに`AppContextSwitchOverrides`要素を追加する代わりに、(C# の場合)または`static``Shared`(Visual Basic の<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>) メソッドを呼び出して、プログラムによってスイッチを設定することもできます。

 ライブラリ開発者は、カスタム スイッチを定義して、呼び出し元がライブラリの以降のバージョンで導入された変更された機能をオプトアウトできるようにすることもできます。 詳細については、<xref:System.AppContext> クラスを参照してください。

## <a name="switches-in-aspnet-applications"></a>ASP.NETアプリケーションのスイッチ

web.config ファイルの[\<appSettings>](../appsettings/index.md)セクションに[\<[>の追加]](../appsettings/add-element-for-appsettings.md)要素を追加することで、互換性設定を使用するようにASP.NET アプリケーションを構成できます。

次の例では、`<add>`要素を使用して、web.config ファイルの`<appSettings>`セクションに 2 つの設定を追加します。

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>例

 次の例では、`AppContextSwitchOverrides`要素を使用して、非同期メソッド呼び`Switch.System.Globalization.NoAsyncCurrentCulture`出しでスレッド間でカルチャが流れないようにする単一のアプリケーション互換性スイッチ を定義します。

```xml
<configuration>
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />
   </runtime>
</configuration>
```

 次の例では、`AppContextSwitchOverrides`この要素を使用して 2 つの`Switch.System.Globalization.NoAsyncCurrentCulture`アプリケーション`Switch.System.IO.BlockLongPaths`互換性スイッチと を定義します。 セミコロンは、2 つの名前と値のペアを区切ります。

```xml
<configuration>
    <runtime>
       <AppContextSwitchOverrides
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />
    </runtime>
</configuration>
```

## <a name="see-also"></a>関連項目

- <xref:System.AppContext?displayProperty=nameWithType>
- [\<ランタイム>要素](runtime-element.md)
- [\<要素>構成](../configuration-element.md)
