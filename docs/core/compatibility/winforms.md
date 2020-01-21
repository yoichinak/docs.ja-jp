---
title: Windows フォームに関する破壊的変更 - .NET Core
description: .NET Core 用の Windows フォームにおける破壊的変更の一覧を示します。
ms.date: 01/08/2020
ms.openlocfilehash: 44bcde60f9e08d2e06a69c55e4ebe904bf5c449b
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116459"
---
# <a name="breaking-changes-in-windows-forms"></a>Windows フォームでの破壊的変更

Windows フォームのサポートは、.NET Core にバージョン 3.0 で追加されました。 この記事では、Windows フォームの破壊的変更を、導入された .NET Core のバージョン別に説明します。 .NET Framework または以前のバージョンの .NET Core (3.0 以降) から Windows フォーム アプリをアップグレードする場合は、この記事が適用されます。

このページでは、次の破壊的変更について説明します。

- [削除されたコントロール](#removed-controls)
- [ヒントが表示されていると CellFormatting が発生しない](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control.DefaultFont を Segoe UI 9 pt に変更](#default-control-font-changed-to-segoe-ui-9-pt)
- [FolderBrowserDialog の最新化](#modernization-of-the-folderbrowserdialog)
- [一部の Windows フォーム型から SerializableAttribute を削除](#serializableattribute-removed-from-some-windows-forms-types)
- [AllowUpdateChildControlIndexForTabControls 互換性スイッチがサポートされない](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [DomainUpDown.UseLegacyScrolling 互換性スイッチがサポートされない](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [DoNotLoadLatestRichEditControl 互換性スイッチがサポートされない](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [DoNotSupportSelectAllShortcutInMultilineTextBox 互換性スイッチがサポートされない](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [DontSupportReentrantFilterMessage 互換性スイッチがサポートされない](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [EnableVisualStyleValidation 互換性スイッチがサポートされない](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [UseLegacyContextMenuStripSourceControlValue 互換性スイッチがサポートされない](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [UseLegacyImages 互換性スイッチがサポートされない](#uselegacyimages-compatibility-switch-not-supported)
- [AccessibleObject.RuntimeIDFirstItem のアクセスに対する変更](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [Windows フォームからの重複する API の削除](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a>関連項目

- [Windows フォーム アプリを .NET Core に移植する](../porting/winforms.md)
