---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449404"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>FileSystemInfo.Attributes によってスローされる UnauthorizedAccessException

.NET Core では、呼び出し元がファイル属性値を設定しようとして、書き込みアクセス許可がない場合、<xref:System.UnauthorizedAccessException> がスローされます。

#### <a name="change-description"></a>変更の説明

.NET Framework では、呼び出し元が <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> でファイル属性値を設定しようとして、書き込みアクセス許可がない場合、<xref:System.ArgumentException> がスローされます。 .NET Core では、代わりに <xref:System.UnauthorizedAccessException> がスローされます (.NET Core では、呼び出し元が無効なファイル属性を設定しようとした場合でも <xref:System.ArgumentException> がスローされます)。

#### <a name="version-introduced"></a>導入されたバージョン

1

#### <a name="recommended-action"></a>推奨アクション

必要に応じて、<xref:System.ArgumentException> の代わりに、または追加として、<xref:System.UnauthorizedAccessException> をキャッチするように `catch` ステートメントを変更します。

#### <a name="category"></a>カテゴリ

CoreFx

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
