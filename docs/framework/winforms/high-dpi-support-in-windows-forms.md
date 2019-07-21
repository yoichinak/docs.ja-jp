---
title: Windows フォームで高 DPI のサポート
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1641702c7b1c3d3b0e83c59a96529de70f699d17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966947"
---
# <a name="high-dpi-support-in-windows-forms"></a>Windows フォームで高 DPI のサポート

.NET Framework 4.7 以降、Windows フォームには、一般的な高 DPI や動的 DPI の状況に応じた機能強化が含まれています。 これには次が含まれます。

- <xref:System.Windows.Forms.MonthCalendar> コントロールや <xref:System.Windows.Forms.CheckedListBox> コントロールなど、多数の Windows フォーム コントロールのスケーリングとレイアウトの改善。

- 単一パスのスケーリング。.NET Framework 4.6 以前のバージョンでは、スケーリングは複数パスにより実行され、必要以上のスケーリングを一部のコントロールに引き起こしていました。

- Windows フォーム アプリケーションが起動された後に、ユーザーによりDPIやスケールファクターが変更される、動的DPIの状況に対応。

.NET Framework 4.7 以降のバージョンでは、高DPI対応の強化はオプトインの機能です。この機能を活用するには、アプリケーションの構成が必要です。

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>高 DPI のサポートを Windows フォーム アプリの構成

高 DPI 対応をサポートする Windows フォームの新しい機能は、.NET Framework 4.7 を対象し、Windows 10 Creators Update 以降の Windows オペレーティング システムで実行しているアプリケーションでのみ使用できます。

さらに、Windows フォーム アプリケーションで高 DPI のサポートを構成するにする必要があります、次のように行います。

- Windows 10 と互換性を宣言します。

  これを行うには、マニフェスト ファイルに、次を追加します。

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- モニターごとの DPI 認識を有効にする、 *app.config*ファイル。

  Windows フォームが導入されていますが、新しい[ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../configure-apps/file-schema/winforms/index.md)の新機能と .NET Framework 4.7 以降では追加のカスタマイズをサポートする要素。 高 DPI をサポートする新しい機能を利用するには、アプリケーション構成ファイルに、次を追加します。

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > .NET Framework の以前のバージョンでは、マニフェストを使用して、高 DPI のサポートを追加します。 このアプローチは推奨されなく app.config ファイルで定義された設定をオーバーライドするためです。

- 呼び出す静的<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッド。

  これは、アプリケーションのエントリ ポイントでは、最初のメソッド呼び出しでなければなりません。 例えば:

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>個々 の高 DPI 機能を無効にします。

設定、`DpiAwareness`値を`PerMonitorV2`.NET Framework 4.7 以降では .NET Framework のバージョンでサポートされている、すべての高 DPI 認識の機能を有効にします。 通常、これは、ほとんどの Windows フォーム アプリケーションに適しています。 ただし、1 つまたは複数の個々 の機能を無効にすることがあります。 これを行うための最も重要な理由は、既存のアプリケーション コードは、その機能を既に処理です。  たとえば、アプリケーションでは、自動スケーリングを処理する場合は次のように、自動サイズ変更機能を無効にします。

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

個々 のキーおよび値の一覧は、次を参照してください。 [Windows フォームの追加の構成要素](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)します。

## <a name="new-dpi-change-events"></a>新しい DPI 変更イベント

3 つの新しいイベントは、.NET Framework 4.7 以降では、プログラムによって動的 DPI の変更を処理することができます。

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>を親コントロールの DPI 変更イベントの後に、コントロールの DPI 設定がプログラムで変更またはフォームが発生したときに発生します。
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>を親コントロールの DPI 変更イベントの前に、コントロールの DPI 設定がプログラムで変更またはフォームが発生したときに発生します。
- <xref:System.Windows.Forms.Form.DpiChanged>、フォームが現在表示されているディスプレイ デバイスの DPI 設定が変更されたときに、これが発生します。

## <a name="new-helper-methods-and-properties"></a>新しいヘルパー メソッドとプロパティ

.NET Framework 4.7 では、さまざまな DPI スケールに関する情報を提供し、DPI スケールを実行できるようにする新しいヘルパー メソッドとプロパティも追加します。 不足している機能には次が含まれます。

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>を論理座標から値をデバイス ピクセルに変換します。

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>、ビットマップ イメージにデバイスの論理 DPI スケールします。

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>を現在のデバイスの DPI が返されます。

## <a name="versioning-considerations"></a>バージョン管理に関する考慮事項

.NET Framework 4.7 と Windows 10 Creators Update でを実行するだけでなく、アプリケーションもない高 DPI 機能強化と互換性のある環境で実行できます。 この場合、代替のアプリケーションを開発する必要があります。 実行するために行うことができます[カスタム描画](./controls/user-drawn-controls.md)スケーリングを処理します。

これを行うには、アプリが実行されているオペレーティング システムを決定する必要があります。 次のようなコードで行うことができます。

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

エントリのアプリケーション マニフェストでサポートされているオペレーティング システムとして表示されていない場合、アプリケーションはありません Windows 10 が検出が正常に注意してください。

アプリケーションがビルドされた .NET Framework のバージョンをチェックすることもできます。

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>関連項目

- [Windows フォームの構成要素を追加します。](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [Windows フォームのサイズとスケールを調整する](adjusting-the-size-and-scale-of-windows-forms.md)
