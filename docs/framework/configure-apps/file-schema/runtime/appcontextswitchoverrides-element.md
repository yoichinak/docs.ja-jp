---
title: <AppContextSwitchOverrides> 要素
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fe354a929aad93ba4d4a6ea3cb43b2607be1f05
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252871"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides > 要素
<xref:System.AppContext> クラスで使用される、新機能に対するオプトアウト メカニズムを指定するスイッチを 1 つまたは複数定義します。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<ランタイム >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<AppContextSwitchOverrides >**  
  
## <a name="syntax"></a>構文  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`value`|必須の属性です。<br /><br /> 1つ以上のスイッチ名とそれに関連付けられたブール値を定義します。|  
  
### <a name="value-attribute"></a>value 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|"name=value"|定義済みのスイッチ名とその値 (`true`また`false`は)。 複数のスイッチの名前と値のペアは、セミコロン (";") で区切られます。 .NET Framework でサポートされている定義済みスイッチ名の一覧については、「解説」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework 4.6 以降、 `<AppContextSwitchOverrides>`構成ファイルの要素を使用すると、API の呼び出し元は、アプリが新しい機能を利用できるか、ライブラリの以前のバージョンとの互換性を維持できるかを判断できます。 たとえば、api の動作がライブラリ`<AppContextSwitchOverrides>`の2つのバージョン間で変更されている場合、要素を使用すると、その api の呼び出し元は、新しい機能をサポートするライブラリのバージョンで新しい動作を無効にすることができます。 .NET Framework で api を呼び出すアプリの場合は、 `<AppContextSwitchOverrides>`要素を使用して、アプリが以前のバージョンの .NET Framework をターゲットにしている呼び出し元が、そのアプリを含む .NET Framework のバージョンで実行されている場合に、新しい機能をオプトインすることもできます。機.  
  
 要素の属性は`value` 、セミコロンで区切られた1つ以上の名前と値のペアで構成される1つの文字列で構成されます。 `<AppContextSwitchOverrides>`  各名前は互換性スイッチを識別し、対応する値は、スイッチ`true`が`false`設定されているかどうかを示すブール値 (または) です。 既定では、スイッチは`false`で、ライブラリは新しい機能を提供します。 スイッチが設定されている場合 (つまり、値が`true`である場合) にのみ、以前の機能が提供されます。 これにより、ライブラリは既存の API に新しい動作を提供できるようになり、以前の動作に依存する呼び出し元は新しい機能を無効にすることができます。  
  
 .NET Framework では、次のスイッチがサポートされています。  
  
|スイッチ名|説明|生まれ|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|コントロールレイアウトのために Windows Presentation Foundation レガシアルゴリズムを使用するかどうかを制御します。 詳細については、「[軽減策:WPF レイアウト](../../../migration-guide/mitigation-wpf-layout.md)。|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|PackageDigitalSignatureManager によってパッケージの部分に署名するために使用される既定のアルゴリズムが SHA1 と SHA256 のどちらであるかを制御します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|に`false`設定すると、FIPS が有効になっている場合に、Visual Studio で XAML ベースのワークフロープロジェクトをデバッグできるようになります。 これを使用し<xref:System.NullReferenceException>ない場合、は、system.object アセンブリ内のメソッドの呼び出しでスローされます。|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|デバッガーのワークフローインスタンスのチェックサムで MD5 と SHA1 のどちらを使用するかを制御します。 | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|ワークフローチェックサムハッシュで、.NET Framework 4.7 (`true`) の既定値として導入された SHA1 アルゴリズムを使用するか、.NET Framework 4.8 (`false`) で既定値として導入された既定の SHA256 アルゴリズムを使用するかどうかを制御します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|移植可能な Pdb を使用するときにスタックトレースが取得するかどうかを制御します。ソースファイルと行情報を含めることができます。 `false`ソースファイルと行情報を含める場合は。それ以外`true`の場合は。|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|オブジェクトに<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.Drawing.Icon> PNG フレームが含まれている場合に、メソッドが例外をスローするかどうかを制御します。 詳細については、「[軽減策:Icon オブジェクト](../../../migration-guide/mitigation-png-frames-in-icon-objects.md)の PNG フレーム。|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|メソッドによってコレクションに追加されたときにオブジェクトが正しく破棄されるかどうか<xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType>を判断します。 <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> `true`従来の動作を維持するには`false`すべてのプライベートフォントオブジェクトを破棄する場合は。 |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|の<xref:System.Windows.Forms.PrintPreviewDialog>パフォーマンスをネットワークプリンター用に最適化するかどうかを制御します。 詳細については、「 [Printプレビューダイアログコントロールの概要](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md)」を参照してください。|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|日本語の暦の時代 (年号) をチェックするかどうかを制御します。 `true`年範囲のチェックを強制する`false`場合は。それを無効にする場合は (既定の動作)。 詳細については、「[カレンダーの操作](../../../../standard/datetime/working-with-calendars.md)」を参照してください。|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|解析操作で、"1" だけを日本語の暦時代 (年号) の最初の年として認識するかどうかを制御します。 `true`"1" だけを認識する場合は。`false` "1" またはガント (既定の動作) のいずれかを認識します。 詳細については、「[カレンダーの操作](../../../../standard/datetime/working-with-calendars.md)」を参照してください。|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|日本語の暦時代 (年号) の最初の年を、書式設定操作で "1" または "ガント" として表示するかどうかを制御します。 `true`時代 (年号) の最初の年を "1" として書式設定するには、`false` (既定の動作) として書式設定します。 詳細については、「[カレンダーの操作](../../../../standard/datetime/working-with-calendars.md)」を参照してください。|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|非同期操作が呼び出し元スレッドのコンテキストからフローされないかどうかを制御します。 詳細については、「[タスク間の CurrentCulture と CurrentUICulture flow](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks)」を参照してください。|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|メソッドが<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType>要求の種類と最後の DNS エントリのみを照合するかどうかを制御します。 詳細については、「[軽減策:X509certificateclaimset.findclaims は、メソッド](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)。|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|AuthorizationContext. Empty を使用して変更可能なオブジェクトを返すかどうかを制御します。|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|よりも`MAX_PATH`長いパス (260 文字) がをスロー <xref:System.IO.PathTooLongException>するかどうかを制御します。 詳細については、「[長いパスのサポート](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support)」を参照してください。|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|<xref:System.IO.Compression.DeflateStream>クラスによる展開にネイティブ OS ルーチンを使用するかどうかを制御します。 `false`ネイティブ Api を使用するには実装を使用する場合は<xref:System.IO.Compression.DeflateStream>。 `true`|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|は、スラッシュ ("\\/") ではなく円記号 ("") を<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>プロパティのパス区切り記号として使用します。 詳細については[、「軽減策:ZipArchiveEntry パスの区切り記号](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)。|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|ストリームで<xref:System.IO.Ports.SerialPort>作成されたバックグラウンドスレッドでスローされるオペレーティングシステムの例外がプロセスを終了するかどうかを制御します。|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|従来の<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType>パスの正規化を使用するかどうか、およびメソッドと<xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>メソッドで URI パスをサポートするかどうかを制御します。 詳細については、「[軽減策:パスの](../../../migration-guide/mitigation-path-normalization.md)正規化[と軽減策:パスのコロン](../../../migration-guide/mitigation-path-colon-checks.md)チェック。|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|等しいかどうかのテストが、 <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> 1 つのオブジェクトのプロパティ<xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType>を2番目のオブジェクトのプロパティと比較するかどうかを制御します。 詳細については、「 [MemberDescriptor の不適切な実装](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals)」を参照してください。|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|証明書の拡張キー使用法 (EKU) の検証を無効にします。 EKU (拡張キー使用法) 拡張は、キーを使用するアプリケーションを示すオブジェクト識別子 (OID) の集まりです。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|SCH_SEND_AUX_RECORD の使用を無効にして、SSL/TLS (利用) の軽減策に対する TLS 1.0 ブラウザーの悪用を無効にします。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|<xref:System.Net.ServicePointManager?displayProperty=nameWithType> および<xref:System.Net.Security.SslStream?displayProperty=nameWithType>クラスが SSL 3.0 プロトコルを使用できるかどうかを制御します。 詳細については、「[軽減策:TLS Protocols (軽減策: TLS プロトコル)](../../../migration-guide/mitigation-tls-protocols.md)」をご覧ください。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|既定の Tls12、Tls11、Tls に戻す SystemDefault TLS のバージョンを無効にします。|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|System.net.security.sslstream TLS サーバー側アラートを無効にします。|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|COM 相互運用イベントの ByRef SafeArray パラメーターがネイティブコードにマーシャリングされる`false`か ()、またはネイティブコードへのマーシャリング`true`が無効になるか () を制御します。|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |[DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer)が ECMAScript V6 と V8 標準に基づいて一部の制御文字をシリアル化するかどうかを制御します。 詳細については、「[軽減策:DataContractJsonSerializer を使用した制御文字のシリアル化](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|で複数の<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>調整をサポートするか、タイムゾーンに対して1つの調整のみをサポートするかを制御します。 の`true`場合、 <xref:System.TimeZoneInfo>型を使用して日付と時刻のデータをシリアル化および逆シリアル化<xref:System.TimeZone>します。それ以外の場合は、複数の調整規則をサポートしていない型を使用します。|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|がオブジェクト<xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType>のシリアル化と逆シリアル化の間に、より大きな配列サイズを使用するかどうかを制御します。 `true` など<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>の型によってラージオブジェクトグラフのシリアル化と逆シリアル化のパフォーマンスを向上させるには、このスイッチをに設定します。 |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|コンストラクターが<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType>新しいオブジェクトの<xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType>プロパティに既存のオブジェクト参照を設定するかどうかを制御します。 詳細については、「[軽減策:ClaimsIdentity コンストラクター](../../../migration-guide/mitigation-claimsidentity-constructor.md)。|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|<xref:System.Security.Cryptography.AesCryptoServiceProvider>復号化を再利用しようとしたが<xref:System.Security.Cryptography.CryptographicException>をスローするかどうかを制御します。 詳細については、「 [AesCryptoServiceProvider の復号化による再利用可能な変換の提供](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform)」を参照してください。|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|[Cspparameters.parentwindowhandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle)プロパティの値が、ウィンドウハンドルのメモリ位置を表す[IntPtr](xref:System.IntPtr)であるか、またはウィンドウハンドル (HWND) であるかを制御します。 詳細については、「[軽減策:CspParameters. Cspparameters.parentwindowhandle には HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value)が必要です。 |.NET Framework 4.7|   
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|FIPS モードでマネージ暗号化クラスを使用するかどうかを<xref:System.Security.Cryptography.CryptographicException>制御`true`します ()。または、システムライブラリ`false`() の実装に依存します。|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|一部の SignedCMS 操作の既定値が SHA1 または SHA256 であるかどうかを判断します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|オペレーティングシステムで<xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType>サポートされているすべての名前付き曲線 (`false`) を正しく処理するか、レガシ動作に戻すかを制御します。|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|一部の SignedXML 操作の既定値が SHA1 または SHA256 であるかどうかを判断します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|セキュリティモードで`TransportWithMessageCredential` 、署名されていない "to" ヘッダーを持つメッセージを許可するかどうかを決定します。 これはオプトインスイッチです。 詳細については、「 [.NET Framework 4.6.1 におけるランタイムの変更点](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf)」を参照してください。|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|要素のいずれ<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>かが`null`の<xref:System.ArgumentException>場合に、コンストラクターがをスローするかどうかを制御します。|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|.CSG キー記憶域プロバイダーで X509 証明書を使用しようとしたときに例外がスローされるかどうかを判断します。 詳細については、「 [WCF トランスポートセキュリティで CNG を使用して格納される証明書をサポート](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng)する」を参照してください|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|自己ホスト型サービスで HTTP トランスポートを使用する場合、この値をに`true`設定すると、要求の応答ヘッダー `Connection: close`にヘッダーを追加するアプリケーションが WCF によって無視されます。 この値をに`false`設定すると`Connection: close` 、応答ヘッダーにヘッダーを追加できるようになります。これにより、応答の送信後に要求ソケットが閉じられます。|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|再入可能サービスのインスタンスを一度に1つの実行スレッドに制限することによって発生するデッドロックを処理します。|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|と共`Switch.System.Net.DontEnableSchUseStrongCrypto`に、WCF メッセージセキュリティが tls 1.1 と tls 1.2 を使用するかどうかを決定します。|.NET Framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|の値は`false` 、オペレーティングシステムがプロトコルを選択できるようにするための既定の構成を設定します。 値をに`true`設定すると、既定値が使用可能な最も高いプロトコルに設定されます。 (以前のバージョンの framework のサービスブランチでも利用可能)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|WCF の MSMQ メッセージの既定のメッセージ署名アルゴリズムが SHA1 であるか SHA256 であるかを判断します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|WCF が SHA1 または SHA256 ハッシュを使用して名前付きパイプのランダムな名前を生成するかどうかを制御します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|例外メッセージが null の場合に[NullReferenceException](xref:System.NullReferenceException)をスローするかどうかを制御します。|.NET Framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|サービスの起動時にスローされる例外が<xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>メソッドの呼び出し元に反映されるかどうかを制御します。|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|インスタンスが<xref:System.Threading.Timer>大規模な環境でパフォーマンスの向上を利用できるかどうかを制御します。 の`true`場合、パフォーマンスの向上が有効に`false`なります。 (既定値) の場合は無効になります。|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|デコードされた可能性がある特定のパーセントエンコード文字が一貫してエンコードされているかどうかを判断します。 の`true`場合は、デコードされます`false`。それ以外の場合は。|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Uri での Unicode の双方向文字の処理を決定します。 `true`Uri から削除するには`false`を保持し、パーセントエンコードします。|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Windows Presentation Foundation が古いアルゴリズム (`true`) を適用するか、または新しいアルゴリズム (`false`) を適用\*して領域を列に割り当てるかを決定します。 詳細については、「[軽減策:グリッドコントロールのスター型列](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns)への領域の割り当て。 |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|選択変更イベントを発生させる前に、セレクターまたはタブコントロールが、選択した値プロパティの値を常に更新するかどうかを制御します。|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Occluded <xref:System.Windows.Controls.TextBox> text ( <xref:System.Windows.Controls.PasswordBox> `true`) を防ぐために、コントロールおよびコントロールに対して非装飾ベースの選択の表示を使用できるかどうかを決定します。または、テキストを装飾層 () でのみ表示するかどうかを指定します。`false`|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|カスタム IList インデクサーをクラスによって正しく`false`使用しない (`true`) か、 <xref:System.Windows.Data.Binding?displayProperty=nameWithType>または正しく () 使用するかを制御します。|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|DPI の変更がシステムごと (の`false`値) またはモニター単位 (の`true`値) のどちらで行われるかを決定します。|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|WPF がモニターごとに認識されるモード<xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType>で実行さ`true`れるときに、内のコントロールのサイズ変更を改善するか`false`どうかを制御します () または有効 ()。|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|コントロールテキストが存在する場合に、 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>開発者がアクションを特別に処理する必要があるかどうかを判断します。 `true`<xref:System.Windows.Forms.DomainUpDown.UpButton>アクションを処理するには`false` とアクションが正常に同期される<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>ようにします。 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>メソッドが呼び出されたときに例外が<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>スローされることなく、カスタム実装がメッセージを安全にフィルター処理できるようにするコードを選択します。 詳細については、「[軽減策:カスタムのの imessagefilter.prefiltermessage 実装](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|ユーザーが入れ子<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>になっ<xref:System.Windows.Forms.ToolStripMenuItem>たコントロールからメニューを開いたときに、プロパティがソース管理を返すかどうかを決定します。 `true`これを`null`返すには、従来の動作です。`false`ソース管理を返す場合は。|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|ツールヒントの呼び出しサポートを無効 (`true`) または有効`false`() にするかどうかを制御します。 ツールヒントの呼び出しサポートを有効にするには`Switch.UseLegacyAccessibilityFeatures`、 `Switch.UseLegacyAccessibilityFeatures.2`、、およびで定義されて`false`いる従来のユーザー補助機能も必要と`Switch.UseLegacyAccessibilityFeatures.3`なります (に設定)。|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|WPF アプリケーションでオプション`WM_POINTER`ベースのタッチ/スタイラススタックを有効にするかどうかを決定します。 詳細については、「[軽減策:ポインターベースのタッチおよびスタイラスのサポート](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|チェックサムに使用される既定のハッシュアルゴリズムが SHA256`false`() または`true`SHA1 () であるかどうかを判断します。<br>SHA1 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|例外の原因 ( [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException)や[FileNotFoundException](xref:System.IO.FileNotFoundException)など) をより具体的に示す例外の代わりに、レガシ[NullReferenceException](xref:System.NullReferenceException)をスローするかどうかを制御します。 これは、 [NullReferenceException](xref:System.NullReferenceException)の処理に依存するコードによって使用されることを意図しています。 | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|ワークフロープロジェクトビルド内の XOML ファイルのチェックサムハッシュが MD5 アルゴリズム (`true`) を使用するかどうか、または .NET Framework 4.8 で既定値として導入された SHA256 アルゴリズムを使用するかどうかを制御します。<br>MD5 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Sqltrackingservice によるチェックサムハッシュで、キャッシュされた`true`文字列に MD5 アルゴリズム () を使用するか、.NET Framework 4.8 で既定値として導入される SHA256 アルゴリズムを使用するかどうかを制御します。<br>MD5 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|ワークフローランタイムによるチェックサムハッシュが、キャッシュされた`true`ワークフロー定義に MD5 アルゴリズム () を使用するかどうか、または .NET Framework 4.8 で既定値として導入された SHA256 アルゴリズムを使用するかどうかを制御します。<br>MD5 との競合問題のため、Microsoft では SHA256 を推奨しています。|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|.NET Framework 4.7.1 で使用できるユーザー補助機能を有効にするか無効にするかを制御します。 | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|.NET Framework 4.7.2 で使用できるユーザー補助機能を有効に`false`するかどうか`true`を制御します () または disabled ()。 の`true`場合`Switch.UseLegacyAccessibilityFeatures`は、.NET Framework `true` 4.7.1 アクセシビリティ機能も有効にする必要があります。|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|.NET Framework 4.8 で導入されたユーザー補助機能が`false`有効かどうか`true`を制御します ()。または disabled ()。 の`true`場合`Switch.UseLegacyAccessibilityFeatures` 、および`Switch.UseLegacyAccessibilityFeatures.2`もで`true`ある必要があります。|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|WPF コントロール (`true`) の上にマウスカーソルを置いたときにツールヒントを表示するか、キーボードフォーカスとキーボードショートカットキー (`false`既定の動作) の両方に表示するかを制御します。 .NET Framework 4.8 で実行され、以前のバージョンの .NET Framework を対象とするアプリケーションでは、キーボードフォーカスとショート`Switch.UseLegacyAccessibilityFeatures`カットキーの`Switch.UseLegacyAccessibilityFeatures.3`サポートの両方を`false`有効にするには、 `Switch.UseLegacyAccessibilityFeatures.2`、、およびすべてをに設定する必要があります。|.NET Framework 4.8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|複合キーの空のキーシーケンスが XSD スキーマ検証によって無視されるかどうかを制御します。 詳細については、「[軽減策:XML スキーマの](../../../migration-guide/mitigation-xml-schema-validation.md)検証。|.NET Framework 4.6|  
  
> [!NOTE]
> `AppContextSwitchOverrides`要素をアプリケーション構成ファイルに追加する代わりに、 `static` (でC#は) または`Shared` (Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>メソッドを呼び出すことによって、スイッチをプログラムで設定することもできます。  
  
 ライブラリ開発者はカスタムスイッチを定義して、新しいバージョンのライブラリで導入された機能の変更を呼び出し元がオプトアウトできるようにすることもできます。 詳細については、<xref:System.AppContext> クラスを参照してください。  
  
## <a name="switches-in-aspnet-applications"></a>ASP.NET アプリケーションのスイッチ

Web.config ファイル[の\<appSettings >](../appsettings/index.md)セクションに[ \<Add >](../appsettings/add-element-for-appsettings.md)要素を追加することにより、互換性設定を使用するように ASP.NET アプリケーションを構成できます。 

次の例では`<add>` 、要素を使用して、 `<appSettings>` web.config ファイルのセクションに2つの設定を追加しています。

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>例

 次の例では`AppContextSwitchOverrides` 、要素を使用して単一のアプリケーション`Switch.System.Globalization.NoAsyncCurrentCulture`互換性スイッチを定義しています。これにより、非同期メソッド呼び出しのスレッド間でカルチャをフローできなくなります。  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 次の例では`AppContextSwitchOverrides` 、要素を使用して、 `Switch.System.Globalization.NoAsyncCurrentCulture`とと`Switch.System.IO.BlockLongPaths`いう2つのアプリケーション互換性スイッチを定義します。 セミコロンでは、2つの名前と値のペアが分離されていることに注意してください。  
  
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
- [\<runtime> 要素](runtime-element.md)
- [\<configuration> 要素](../configuration-element.md)
