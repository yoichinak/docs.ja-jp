---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237393"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Microsoft.VisualBasic.Devices 名前空間の型は使用できません

<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> 名前空間の型は使用できません。

#### <a name="version-introduced"></a>導入されたバージョン

.NET Core 3.0 Preview 8

#### <a name="change-description"></a>変更の説明

<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> 名前空間の型は、一部の .NET Core 3.0 プレビュー リリースで使用できました。 .NET Core 3.0 Preview 9 以降では使用できなくなりました。

これらの型は、今後のリリースでの不要なアセンブリの依存関係や破壊的変更を回避するために削除されました。
 
#### <a name="recommended-action"></a>推奨される操作

コードが <xref:Microsoft.VisualBasic.Devices> 型とそのメンバーの使用に依存している場合は、.NET クラス ライブラリ内の対応する型またはメンバーを使用できる可能性があります。 たとえば、<xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> クラスと同等の機能は <xref:System.DateTime?displayProperty=nameWithType> および <xref:System.Environment?displayProperty=nameWithType> 型によって提供されており、<xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> クラスと同等の機能は、<xref:System.IO.Ports?displayProperty=nameWithType> 名前空間の型によって提供されています。

#### <a name="category"></a>カテゴリ

Visual Basic

#### <a name="affected-apis"></a>影響を受ける API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

