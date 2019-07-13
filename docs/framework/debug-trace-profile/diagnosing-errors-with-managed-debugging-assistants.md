---
title: マネージド デバッグ アシスタントによるエラーの診断
ms.date: 08/14/2018
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874623"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>マネージ デバッグ アシスタントによるエラーを診断します。

マネージド デバッグ アシスタント (MDA) は、共通言語ランタイム (CLR: Common Language Runtime) と連携してランタイム状態に関する情報を提供するデバッグ支援ツールです。 MDA は、これ以外の方法ではトラップできないランタイム イベントに関する情報メッセージを生成します。 MDA を使用すると、マネージド コードからアンマネージド コードへの遷移時に発生する、検出が難しいアプリケーション バグを分離できます。

できます[有効または無効に](#enable-and-disable-mdas)すべての Mda を Windows レジストリにキーを追加するか、環境変数を設定します。 特定の MDA を有効にするには、アプリケーション構成設定を使用します。 一部の MDA については、アプリケーションの構成ファイルで追加の構成設定を個別に設定できます。 この構成ファイルはランタイムの読み込み時に解析されるため、MDA は、マネージド アプリケーションが起動する前に有効にする必要があります。 MDA は、既に起動しているアプリケーションに対して有効にできません。

次の表では、.NET Framework に付属する Mda を示します。

|||
|-|-|
|[asynchronousThreadAbort](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[bindingFailure](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|
|[callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|
|[dangerousThreadingAPI](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|
|[dirtyCastAndCallOnInterface](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[disconnectedContext](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|
|[dllMainReturnsFalse](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|
|[failedQI](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[fatalExecutionEngineError](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|
|[gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|
|[illegalPrepareConstrainedRegion](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|
|[invalidCERCall](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|
|[invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|
|[invalidMemberDeclaration](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|
|[invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|
|[loaderLock](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[loadFromContext](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|
|[marshalCleanupError](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|
|[memberInfoCacheCreation](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[moduloObjectHashcode](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|
|[nonComVisibleBaseClass](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[notMarshalable](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|
|[openGenericCERCall](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|
|[pInvokeLog](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|
|[raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[reentrancy](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|
|[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|
|[streamWriterBufferedDataLost](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[virtualCERCall](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|

既定では、.NET Framework はすべてのマネージド デバッガーに対して MDA のサブセットをアクティブにします。 選択すると、Visual Studio で設定した既定値を表示する**Windows** > **例外設定**上、**デバッグ**メニューのおよび、を展開し、**マネージ デバッグ アシスタント**一覧。

![Visual Studio での例外設定ウィンドウ](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>無効にする Mda の有効化と

MDA は、レジストリ キー、環境変数、およびアプリケーション構成設定を使用して有効または無効にできます。 アプリケーション構成設定を使用するには、レジストリ キーまたは環境変数を有効にする必要があります。

> [!TIP]
> Mda を無効にすると、代わりに Visual Studio を防ぐため、MDA 通知を受け取るたびに MDA ダイアログ ボックスが表示されないことができます。 次のように選択します**Windows** > **例外設定**上、**デバッグ**メニューで、展開、**マネージ デバッグ アシスタント**。ボックスの一覧をオンまたはオフ、**スローされたときに中断**個々 の MDA に対してチェック ボックス。

### <a name="registry-key"></a>レジストリ キー

Mda を有効にするには追加、 **hkey_local_machine \software\microsoft\\します.Netframework \mda** Windows レジストリのサブキー (REG_SZ 型、値 1)。 という名前のテキスト ファイルに次の例をコピー *MDAEnable.reg*します。Windows レジストリ エディター (RegEdit.exe) を開くとの間、**ファイル**メニュー**インポート**します。 選択、 *MDAEnable.reg*ファイルをそのコンピューターで Mda を有効にします。 サブキーの設定の文字列値に**1** (の DWORD 値ではなく**1**) から MDA の設定を読み取ることができるように、 *ApplicationName.suffix*.mda.config ファイル。 たとえば、メモ帳の MDA 構成ファイルは notepad.exe.mda.config になります。

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

64 ビット オペレーティング システム上で 32 ビット アプリケーションを実行しているコンピューターでは、MDA キーは次のように設定します。

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

参照してください[アプリケーションに固有の構成設定](#application-specific-configuration-settings)詳細についてはします。 レジストリ設定は、COMPLUS_MDA 環境変数でオーバーライドできます。 参照してください[環境変数](#environment-variable)詳細についてはします。

Mda を無効にする MDA サブキーを設定**0** (0)、Windows レジストリ エディターを使用します。

MDA には、レジストリ キーを追加しなくても、デバッガーにアタッチされているアプリケーションを実行すると既定で有効になるものがあります。 実行してこれらのアシスタントを無効にすることができます、 *MDADisable.reg*ファイルのこのセクションの説明のとおりです。

### <a name="environment-variable"></a>環境変数

MDA のアクティブ化は、COMPLUS_MDA 環境変数によって制御することもできます。この環境変数はレジストリ キーをオーバーライドします。 COMPLUS_MDA の文字列は、MDA 名やその他の特殊制御文字列の、セミコロンで区切られたリストで、大文字小文字の区別はありません。 マネージド デバッガーやアンマネージド デバッガーの下で起動すると、MDA のセットが既定で有効になります。 そのためには、デバッガーの下で既定で有効にする MDA のリスト (セミコロン区切り) を、環境変数またはレジストリ キーの値の前に暗黙的に付加します。 特殊制御文字列は次のとおりです。

- `0` - すべての MDA を非アクティブにします。

- `1` - *ApplicationName*.mda.config から MDA の設定を読み取ります。

- `managedDebugger` - デバッガーの下でマネージド実行可能ファイルを起動すると、暗黙的にアクティブ化されているすべての MDA が明示的にアクティブ化されます。

- `unmanagedDebugger` - デバッガーの下でアンマネージ実行可能ファイルを起動すると、暗黙的にアクティブ化されているすべての MDA が明示的にアクティブ化されます。

競合する設定がある場合は、最新の設定が以前の設定を次のようにオーバーライドします。

- `COMPLUS_MDA=0` は、デバッガーの下で暗黙的に有効化されている MDA を含め、すべての MDA を無効にします。

- `COMPLUS_MDA=gcUnmanagedToManaged` は、デバッガーの下で暗黙的に有効化される MDA に加えて `gcUnmanagedToManaged` も有効にします。

- `COMPLUS_MDA=0;gcUnmanagedToManaged` は `gcUnmanagedToManaged` を有効にしますが、デバッガーの下で別途暗黙的に有効化されている MDA を無効にします。

### <a name="application-specific-configuration-settings"></a>アプリケーション固有の構成設定

アプリケーションの MDA 構成ファイルでは、一部のアシスタントを個別に有効化、無効化、および構成できます。 MDA を構成する目的でアプリケーション構成ファイルの使用を有効にするには、MDA レジストリ キーまたは COMPLUS_MDA 環境変数を設定する必要があります。 アプリケーション構成ファイルは、通常、アプリケーションの実行可能ファイル (.exe) と同じディレクトリに置かれます。 このファイル名の形式は、*ApplicationName*.mda.config です (notepad.exe.mda.config など)。アプリケーション構成ファイルで有効にされたアシスタントには、そのアシスタントの動作を制御するために特別にデザインされた属性や要素が存在する場合があります。

次の例では、有効にして構成する方法を示しています、[マーシャ リング](../../../docs/framework/debug-trace-profile/marshaling-mda.md):

```xml
<mdaConfig>
  <assistants>
    <marshaling>
      <methodFilter>
        <match name="*"/>
      </methodFilter>
      <fieldFilter>
        <match name="*"/>
      </fieldFilter>
    </marshaling>
  </assistants>
</mdaConfig>
```

`Marshaling` MDA では、アプリケーションでのマネージド コードからアンマネージド コードへの遷移ごとに、アンマネージド型にマーシャリングされるマネージド型についての情報が出力されます。 `Marshaling` MDA は、メソッドの名前もをフィルター処理、および構造体のフィールドで、 **methodFilter**と**fieldFilter**子要素では、それぞれします。

次の例では、既定の設定を使用して複数の Mda を有効にする方法を示します。

```xml
<mdaConfig>
  <assistants>
    <illegalPrepareConstrainedRegion />
    <invalidCERCall />
    <openGenericCERCall />
    <virtualCERCall />
  </assistants>
</mdaConfig>
```

> [!IMPORTANT]
> 構成ファイルに複数のアシスタントを指定する場合は、アルファベット順に記述する必要があります。 たとえば、`virtualCERCall` MDA と `invalidCERCall` MDA の両方を有効にする場合は、`<invalidCERCall />` エントリ、`<virtualCERCall />` エントリの順に追加する必要があります。 エントリがアルファベット順になっていない場合、ハンドルされない無効な構成ファイルであることを示す例外メッセージが表示されます。

## <a name="mda-exceptions"></a>MDA 例外

MDA を有効にするがアクティブなもときに、コードが実行されていないのデバッガーの下でします。 デバッガーが存在しない場合に MDA イベントが発生した場合、そのイベントはハンドルされない例外とは異なりますが、イベント メッセージはハンドルされない例外のダイアログ ボックスに表示されます。 このダイアログ ボックスが表示されないようにするには、デバッグ環境でコードを実行しているのではないときに、MDA を有効にする設定を削除します。

Visual Studio 統合開発環境 (IDE) で、コードを実行するときは、特定の MDA イベントについて表示される [例外] ダイアログ ボックスを回避できます。 そのため、**デバッグ**] メニューの [選択**Windows** > **例外設定**します。 **例外設定**ウィンドウで、展開、**マネージ デバッグ アシスタント**、一覧表示し、オフ、**中断するとスローされます**個々 の MDA に対してチェック ボックス。 このダイアログ ボックスを使用することもできます。*を有効にする*MDA 例外ダイアログ ボックスが表示されます。

## <a name="mda-output"></a>MDA の出力

MDA の出力は次の例は、出力を示しますに似ています、 `PInvokeStackImbalance` MDA:

**PInvoke 関数の呼び出し ' MDATest!MDATest.Program::StdCall' が、スタックのバランスが取れていません。これは、マネージ PInvoke シグネチャが非管理対象のターゲットのシグネチャと一致しないために、可能性があります。呼び出し規約と PInvoke シグネチャのパラメーターが、ターゲットのアンマネージ シグネチャを一致するかを確認します。**

## <a name="see-also"></a>関連項目

- [デバッグ、トレース、およびプロファイリング](../../../docs/framework/debug-trace-profile/index.md)
