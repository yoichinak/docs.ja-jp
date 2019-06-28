---
title: Windows フォームの構成要素を追加します。
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75a66ee7ca1d7c99de6e2cc9a1d502ea58dbf9f7
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422823"
---
# <a name="windows-forms-add-configuration-element"></a>Windows フォームの構成要素を追加します。

`<add>`要素は、Windows フォーム アプリが .NET Framework 4.7 以降の Windows フォーム アプリに追加された機能をサポートしているかどうかを指定する定義済みのキーを追加します。

## <a name="syntax"></a>構文

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

| 属性 | 説明 |
| --------- | ----------- |
| `key`     | 必須の属性です。 特定の Windows フォームのカスタマイズ可能な機能に対応する定義済みのキー名。 |
| `value`   | 必須の属性です。 代入する値`key`します。 |

### <a name="key-attribute-names-and-associated-values"></a>`key` 属性の名前と関連付けられている値

| `key` 名 | 値 | 説明 |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | 単一のパスで固定されたコントロールをスケーリングするかどうかを示します。 スケーリング、1 つを無効にするには"true"を渡すそれ以外の場合、false です。 「1 つは、スケーリングを渡す」を参照してください、[解説](#remarks)詳細についてはします。 |
| "DpiAwareness" | "PerMonitorV2"&#124;"false" | アプリケーションが DPI 対応かどうかを示します。 Dpi 対応; をサポートするには、"PerMonitorV2"にキーを設定します。それ以外の場合、"false"に設定します。 DPI 対応は、オプトイン機能です。Windows フォームの高 DPI のサポートを利用するには、"PerMonitorV2"には、その値を設定する必要があります。 参照してください、[解説](#remarks)詳細についてはします。 |
| "CheckedListBox.DisableHighDpiImprovements" | "true"&#124;"false" | 示すかどうか、<xref:System.Windows.Forms.CheckedListBox>コントロールは、.NET Framework 4.7 で導入されたスケーリングとレイアウトの機能強化を活用します。 スケーリングとレイアウトの改善をオプトアウトするには"true"それ以外の場合、"false"です。 |
| "DataGridView.DisableHighDpiImprovements" | "true"&#124;"false" | 示すかどうか、 <xref:System.Windows.Forms.DataGridView> .NET Framework 4.7 で導入された機能強化が拡大縮小とレイアウトを制御します。 DPI 対応; をオプトアウトするには"true""false"それ以外の場合。 |
| "DisableDpiChangedMessageHandling" | "true"&#124;"false" | DPI スケール変更に関連するメッセージの受信をオプトアウトするには"true""false"それ以外の場合。 参照してください、[解説](#remarks)詳細についてはします。 |
| "EnableWindowsFormsHighDpiAutoResizing" | "true"&#124;"false" | Windows フォーム アプリケーションの DPI スケールが変更されたのため自動的にサイズを変更するかどうかを示します。 自動サイズ変更を有効にするのには"true"それ以外の場合、false です。 |
| "Form.DisableSinglePassControlScaling" | "true"&#124;"false" | 示すかどうか、<xref:System.Windows.Forms.Form>は単一のパスでスケーリングされます。 スケーリング、"true"を無効にする単一のパスそれ以外の場合、false です。 「1 つは、スケーリングを渡す」を参照してください、[解説](#remarks)詳細についてはします。 |
| "MonthCalendar.DisableSinglePassControlScaling" | "true"&#124;"false" | 示すかどうか、<xref:System.Windows.Forms.MonthCalendar>コントロールが単一のパスでスケーリングします。 スケーリング、"true"を無効にする単一のパスそれ以外の場合、false です。 「1 つは、スケーリングを渡す」を参照してください、[解説](#remarks)詳細についてはします。 |
| "Toolstrip.DisableHighDpiImprovements" | "true"&#124;"false" | 示すかどうか、<xref:System.Windows.Forms.ToolStrip>コントロールは、.NET Framework 4.7 で導入されたスケーリングとレイアウトの機能強化を活用します。 DPI 対応; をオプトアウトするには"true""false"それ以外の場合。 |

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

| 要素 | 説明 |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | 新しい Windows フォーム アプリケーションの機能のサポートを構成します。 |

## <a name="remarks"></a>Remarks

.NET Framework 4.7 を使用すれば、.NET Framework の最近のリリースで追加された機能が利用できる Windows フォームのアプリケーションを、`<System.Windows.Forms.ApplicationConfigurationSection>` 要素で構成できます。

`<System.Windows.Forms.ApplicationConfigurationSection>`要素では、1 つまたは複数の子を追加できます。`<add>`要素は、それぞれが特定の構成設定を定義します。

Windows フォームの高 DPI サポートの概要については、次を参照してください。 [Windows フォームでの高 DPI サポート](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)します。

### <a name="dpiawareness"></a>DpiAwareness

.NET Framework で導入された 高 DPI 機能強化を活用するために .NET Framework 4.7 以降では Windows 10 Creators Edition と .NET Framework のターゲット バージョン以降の Windows バージョンで実行される Windows フォーム アプリを構成することができます。4.7。 不足している機能には次が含まれます。

- Windows フォーム アプリケーションが起動された後に、ユーザー、DPI またはスケール ファクターを変更、動的 DPI シナリオのサポート。

- スケーリングとさまざまな Windows フォームのレイアウトの機能強化を制御するなど、<xref:System.Windows.Forms.MonthCalendar>コントロールと<xref:System.Windows.Forms.CheckedListBox>コントロール。

高 DPI 対応は、オプトイン機能です。既定の値で`DpiAwareness`は`false`します。 DPI 対応にこのキーの値を設定して Windows フォームのサポートを選択できます`PerMonitorV2`アプリケーション構成ファイルでします。 DPI 対応を有効にすると、個々 のすべての DPI 機能も有効にします。 不足している機能には次が含まれます。

- DPI 変更によって制御される、メッセージ、`DisableDpiChangedMessageHandling`キー。

- によって制御される、動的 DPI のサポート、`EnableWindowsFormsHighDpiAutoResizing`キー。

- 単一のパス コントロールがスケーリングによって制御されますが、`Form.DisableSinglePassControlScaling`個々 の<xref:System.Windows.Forms.Form>コントロールで、 `AnchorLayout.DisableSinglePassControlScaling` 、アンカー コントロールとキー、`MonthCalendar.DisableSinglePassControlScaling`のキー、<xref:System.Windows.Forms.MonthCalendar>コントロール

- 高 DPI スケーリングとレイアウトの機能強化、によって制御される、`CheckListBox.DisableHighDpiImprovements`キー、<xref:System.Windows.Forms.CheckedListBox>コントロールによって、`DataGridView.DisableHighDpiImprovements`のキー、<xref:System.Windows.Forms.DataGridView>コントロール、および、`Toolstrip.DisableHighDpiImprovements`のキー、<xref:System.Windows.Forms.ToolStrip>コントロール。

1 つの既定、オプトイン設定は設定によって提供される`DpiAwareness`に`PerMonitorV2`は一般に、新しい Windows フォーム アプリケーションの適切な。 ただし、ことができますし、オプトアウトする個々 の高 DPI 機能強化、アプリケーション構成ファイルに対応するキーを追加することで。 たとえば、動的 DPI のサポートを除くすべての新しい DPI 機能を利用する場合は、アプリケーション構成ファイルには、次を追加します。

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

通常、オプトアウトする特定の機能をプログラムで処理することを選択したためです。

Windows フォーム アプリケーションの高 DPI サポートの利用の詳細については、次を参照してください。 [Windows フォームでの高 DPI サポート](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)します。

### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

以降、.NET Framework 4.7 では、Windows フォーム コントロールは、数の DPI スケールでの変更に関連するイベントを発生します。 以下の<xref:System.Windows.Forms.Control.DpiChangedAfterParent>、 <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>、および<xref:System.Windows.Forms.Form.DpiChanged>イベント。 値、`DisableDpiChangedMessageHandling`キーは、Windows フォーム アプリケーションで、これらのイベントが発生したかどうかを決定します。

### <a name="single-pass-scaling"></a>単一パスのスケーリング

調整ので、ユーザー インターフェイスの認識される応答性とユーザー インターフェイス要素の視覚的な外観に影響 1 つまたは複数のパスをスケーリングします。 以降、.NET Framework 4.7 では、Windows フォームは、単一のパスのスケーリングを使用します。 .NET Framework の以前のバージョンでスケーリングが必要以上にスケールする一部のコントロールの原因とする複数のパスから実行されました。 アプリが古い動作に依存している場合、単一パス scaling を無効のみ必要があります。

## <a name="see-also"></a>関連項目

- [Windows フォームの構成セクション](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)
- [Windows フォームの高 DPI サポート](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
