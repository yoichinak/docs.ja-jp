---
title: <runtime> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
ms.openlocfilehash: 3ac5fdeaebfd67d6ad4f68166fda588b9e58ca98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704584"
---
# <a name="runtime-element"></a>\<runtime> 要素
アプリケーションを構成する共通言語ランタイムで使用される情報を提供します。  
  
 \<configuration>  
\<runtime>  
  
## <a name="syntax"></a>構文  
  
```xml  
<runtime>  
</runtime>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 次のセクションでは、要素の子および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|偽装の実行方法に関係なく、Windows ID が常に非同期ポイント間でフローすることを指定します。|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|<xref:System.AppContext> クラスで使用される、新機能に対するオプトアウト メカニズムを指定するスイッチを 1 つまたは複数定義します。|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|プロセスにおける既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを提供するアセンブリを指定します。|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーの役割を果たす種類を指定します。|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|プロセスのライフサイクルにおいて、プロセスのすべてのアプリケーション ドメインの統計を収集するようにランタイムに指示します。|  
|[\<assemblyBinding>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|信頼されたアセンブリに対する厳密な名前の検証をバイパスするかどうかを指定します。|  
|[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|文字列比較を実行するときに、ランタイムがレガシ並べ替え動作を使用する必要がありますを指定します。|  
|[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|DEVPATH 環境変数によって指定されたディレクトリで、ランタイムがアセンブリの検索を行うかどうかを指定します。|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|キャッシュ バインディング エラーのある .NET Framework version 2.0 の既定の動作が無効になっているかどうかを指定します。|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|スレッドの起動時にスレッド スタック全体をコミットするかどうかを指定します。|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|アプリケーション ドメインの構成設定をランタイム ホストがオーバーライドする既定の動作を無効化するかどうかを指定します。|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|日付と時刻の解析メソッドが、日、月、時間、および午前/午後のみを含む日付の文字列を解析するように調整されたルールのセットを使用するかどうかを決定します。|  
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|暗号化アルゴリズムが連邦情報処理規格 (FIPS: Federal Information Processing Standard) に準拠する必要があるコンピューターの構成要件を強制するかどうかを指定します。|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|共通言語ランタイム イベントで Windows イベント トレーシング (ETW) を有効にするかどうかを指定します。|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|PerfCounter.dll が、.NET Framework バージョン 1.1 のアプリケーションの CategoryOptions レジストリ設定を使用してするかどうかを指定して、カテゴリ別の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを決定します。|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|64 ビット プラットフォームで、合計サイズが 2 GB (ギガバイト) を超える配列を有効にします。|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|共通言語ランタイムがガベージ コレクションを同時に実行するかどうかを指定します。|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|共通言語ランタイムがサーバーのガベージ コレクションを実行するかどうかを指定します。|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|ランタイムがコード アクセス セキュリティ (CAS) の発行元ポリシーを使用するかどうかを指定します。|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|ランタイムがアクセス違反およびその他の破損状態例外をキャッチするマネージド コードを許可するかどうかを指定します。|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Windows ID が、現在のスレッドの実行コンテキストのフロー設定に関係なく、非同期ポイント間でフローしないことを指定します。|  
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|リモート ソースからのアセンブリを完全な信頼として読み込むかどうかを指定します。|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|ランタイムがレガシ コード アクセス セキュリティ (CAS) ポリシーを使用するかどうかを指定します。|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|ランタイムが実行時の不適切なプラットフォーム呼び出し宣言を自動的に修正するかどうかを指定します。これにより、マネージド コードとアンマネージド コード間の遷移が遅くなります。|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドで固定量のメモリを使用してハッシュ コードを計算するかどうかを指定します。|  
|[\<PreferComInsteadOfRemoting >](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|ランタイムが、アプリケーション ドメインの境界間のリモート処理ではなく COM 相互運用を使用することを指定します。|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|サテライト アセンブリのプローブを最適化します。|  
|[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|シャドウ コピーが [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] で導入された既定の起動の動作を使用するか、.NET Framework の以前のバージョンの起動の動作に戻すかどうかを指定します。|  
|[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|.NET Framework の 2 つの異なる実装にある同じアセンブリを 1 つのアプリケーションから参照できるように、既定の動作を無効にすることができます。既定の動作では、アプリケーションの移植性を高めるために、このようなアセンブリは同等のものとして扱われます。|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|既定のメモリ内オブジェクト キャッシュの構成情報を提供します。|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|ランタイムによって、すべての CPU グループにマネージド スレッドを分散するかどうかを指定します。|  
|[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|タスクがハンドルされない例外によって実行中のプロセスを終了するかどうかを指定します。|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|ランタイムで <xref:System.TimeSpan> の値に従来の書式を使用するかどうかを指定します。|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|共通言語ランタイムが Just-In-Time コンパイルの従来の 64 ビット JIT コンパイラを使用するかどうかを決定します。|  
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|ランタイムがアプリケーション ドメインごとに文字列のハッシュ コードを計算するかどうかを指定します。|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|ランタイムが内部的に使用する特定のスレッド作成時に、既定のスタック サイズではなく明示的なスタック サイズを使用することを要求します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="remarks"></a>Remarks  
 内の子要素、 [\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)構成ファイルのセクションは、アプリケーションを実行する方法を構成する共通言語ランタイムによって使用されます。 たとえば、 [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)要素は、ガベージ コレクターがワークステーションのガベージ コレクションまたはサーバーのガベージ コレクションを使用するかどうかを決定、 [ \<UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)要素は、共通言語ランタイムがアプリケーションごと、またはアプリケーションごとのドメインごとに文字列のハッシュ コードを計算するかどうかを決定し、`AppContextSwitchOverrides`要素により、ライブラリ ユーザー有効または無効にするライブラリによって提供される変更された機能です。  
  
 内の要素、 [\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)セクションは、アプリケーションの起動時に、共通言語ランタイムによって自動的に読み取られます。 その名前を指定することによって、既定以外のアプリケーション ドメインの構成ファイルを定義することも、<xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType>プロパティの設定は、アプリケーション ドメインが読み込まれるときに自動的に読み込まれます。 まれには場合、これまでが必要で設定を直接読み取る必要がある、 [\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)アプリケーションの構成ファイルでセクション。  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
