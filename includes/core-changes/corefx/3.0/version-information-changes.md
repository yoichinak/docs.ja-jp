---
ms.openlocfilehash: 1580c8c8b7bdad91656f494537230293dbaaf93b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021618"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>バージョンをレポートする API が、ファイル バージョンではなく製品をレポートするようになりました

.NET Core のバージョンを返す API の多くは、ファイル バージョンではなく製品バージョンを返すようになりました。

#### <a name="change-description"></a>変更の説明

.NET Core 2.2 およびそれ以前のバージョンでは、<xref:System.Environment.Version?displayProperty=nameWithType>、<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> などのメソッドと、.NET Core アセンブリの [ファイルのプロパティ] ダイアログにファイルのバージョンが反映されています。 .NET Core 3.0 以降では、製品のバージョンが反映されています。

次の図は、.NET Core 2.2 (左側) と .NET Core 3.0 (右側) の *System.Runtime.dll* アセンブリのバージョン情報の違いを示しています。これは、**Windows Explorer** [ファイルのプロパティ] ダイアログに表示されます。

![製品バージョン情報の相違点](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="recommended-action"></a>推奨アクション

なし。 この変更により、機能性ではなく、バージョン検出を直感的に行う必要があります。

#### <a name="category"></a>カテゴリ

Core .NET ライブラリ

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
