---
title: PrintPreviewDialog コントロールの概要 (Windows フォーム)
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 961b3c852f60a0917707bef07d4e26fc4215acca
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611121"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog コントロールの概要 (Windows フォーム)

Windows フォーム<xref:System.Windows.Forms.PrintPreviewDialog>コントロールは、構成済みのダイアログ ボックスを表示するために使用する方法、 [PrintDocument](printdocument-component-windows-forms.md)印刷されたときに表示されます。 ダイアログ ボックスを構成する代わりに単純なソリューションとして、Windows ベースのアプリケーションの中で使用します。 このコントロールには、印刷を開始するボタン、ズーム イン用のボタン、1 ページまたは複数ページを表示するボタン、およびダイアログ ボックスを閉じるためのボタンが含まれています。

## <a name="key-properties-and-methods"></a>キー プロパティとメソッド

コントロールのキー プロパティは、<xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>をプレビューするドキュメントを設定します。 ドキュメントがある必要があります、<xref:System.Drawing.Printing.PrintDocument>オブジェクト。 ダイアログ ボックスを表示するために呼び出す必要があるその<xref:System.Windows.Forms.Form.ShowDialog%2A>メソッド。 アンチエイリアシングが滑らかにテキストを行うことができますが、低速です。 表示することもできますが、これを使用する設定、<xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A>プロパティを`true`します。

特定のプロパティは、<xref:System.Windows.Forms.PrintPreviewControl>を<xref:System.Windows.Forms.PrintPreviewDialog>が含まれています。 (これを追加する必要はありません<xref:System.Windows.Forms.PrintPreviewControl>フォームに自動的に格納されて、<xref:System.Windows.Forms.PrintPreviewDialog>ダイアログ ボックスをフォームに追加するとします)。利用できるプロパティの例については、<xref:System.Windows.Forms.PrintPreviewControl>は、<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>と<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>プロパティで、コントロールの水平および垂直を表示するページの数を決定します。 アクセスできる、<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>プロパティとして`PrintPreviewDialog1.PrintPreviewControl.Columns`Visual basic で`printPreviewDialog1.PrintPreviewControl.Columns`ビジュアルC#、または`printPreviewDialog1->PrintPreviewControl->Columns`で[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]します。

## <a name="printpreviewdialog-performance"></a>PrintPreviewDialog パフォーマンス

次の条件下で、<xref:System.Windows.Forms.PrintPreviewDialog>コントロールは非常に遅くなりますを初期化します。

- ネットワーク プリンターが使用されます。
- 双方向の設定など、プリンターのユーザー設定を変更します。

アプリの .NET Framework 4.5.2 で実行されている場合に、次のキーを追加することができます、 \<appSettings > セクションのパフォーマンスを向上させるために、構成ファイルの<xref:System.Windows.Forms.PrintPreviewDialog>の初期化を制御します。

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

場合、`EnablePrintPreviewOptimization`キーが、他の値に設定されているか、キーが存在しない場合、最適化は適用されません。

アプリの .NET Framework 4.6 以降のバージョンで実行されている場合は、次のスイッチを追加することができます、 [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)内の要素、 [\<ランタイム >](../../configure-apps/file-schema/runtime/index.md)アプリ構成ファイルのセクション:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

スイッチが存在しない場合、またはその他の値に設定されている場合は、最適化は適用されません。

使用する場合、<xref:System.Drawing.Printing.PrintDocument.QueryPageSettings>のパフォーマンスのプリンターの設定を変更するイベント、<xref:System.Windows.Forms.PrintPreviewDialog>最適化の構成スイッチが設定されている場合でも、コントロールは改善されません。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [PrintPreviewControl コントロールの概要](printpreviewcontrol-control-overview-windows-forms.md)
- [PrintPreviewDialog コントロール](printpreviewdialog-control-windows-forms.md)
- [ダイアログ ボックス コントロールおよびコンポーネント](dialog-box-controls-and-components-windows-forms.md)
