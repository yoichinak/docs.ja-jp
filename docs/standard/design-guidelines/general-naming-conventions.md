---
title: 一般的な名前付け規則
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: ef4a8f571a67477739bbc59d3103ba78dea47177
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635919"
---
# <a name="general-naming-conventions"></a>一般的な名前付け規則

このセクションでは、単語の選択に関連する一般的な命名規則、略語と略語の使用に関するガイドライン、および言語固有の名前の使用を避ける方法に関する推奨事項について説明します。

## <a name="word-choice"></a>単語の選択
 ✔️は、読みやすい識別子名を選択します。

 たとえば、という名前`HorizontalAlignment`のプロパティは、 より`AlignmentHorizontal`英語で読み取り可能です。

 簡潔✔️よりも読みやすさを優先します。

 プロパティ名`CanScrollHorizontally`は、X`ScrollableX`軸への参照が不明である場合よりも優れています。

 ❌下線、ハイフン、その他の英数字以外の文字は使用しないでください。

 ❌ハンガリー語表記法を使用しないでください。

 ❌広く使用されているプログラミング言語のキーワードと競合する識別子を使用しないでください。

 共通言語仕様 (CLS) の規則 4 に従って、すべての準拠言語は、識別子としてその言語のキーワードを使用する名前付き項目へのアクセスを許可するメカニズムを提供する必要があります。 たとえば、C# では、 @ 記号をエスケープ メカニズムとして使用します。 ただし、エスケープ シーケンスを使用するメソッドを使用する方が、一般的なキーワードを使用しない場合よりも、メソッドを使用する方が難しいため、一般的なキーワードを避けることをお勧めします。

## <a name="using-abbreviations-and-acronyms"></a>略語と頭字語の使用
 ❌識別子名の一部として省略形または短縮を使用しないでください。

 たとえば、 ではなく`GetWindow``GetWin`を使用します。

 ❌広く受け入れられていない頭字語を使用しないでください。

## <a name="avoiding-language-specific-names"></a>言語固有の名前の回避
 ✔️は、型名に言語固有のキーワードではなく、意味的に興味深い名前を使用します。

 たとえば、`GetLength`より`GetInt`良い名前です。

 識別子の型を超えて意味を持たない場合✔️、言語固有の名前ではなく、一般的な CLR 型名を使用します。

 たとえば、変換する<xref:System.Int64>メソッドは、 ではなく`ToInt64`という名前`ToLong`にする<xref:System.Int64>必要があります ( C# 固有のエイリアス`long`の CLR 名であるため ) 。 次の表は、CLR 型名を使用する基本データ型を示しています ( C# 、Visual Basic、および C++ の対応する型名 ) を示します。

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**sbyte**|**SByte**|**char**|**SByte**|
|**byte**|**Byte**|**unsigned char**|**Byte**|
|**short**|**短い**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**Integer**|**int**|**Int32**|
|**uint**|**UInt32**|**unsigned int**|**UInt32**|
|**長い**|**長い**|**__int64**|**Int64**|
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|
|**float**|**Single**|**float**|**Single**|
|**double**|**Double**|**double**|**Double**|
|**bool**|**Boolean**|**bool**|**Boolean**|
|**char**|**Char**|**wchar_t**|**Char**|
|**string**|**String**|**String**|**String**|
|**オブジェクト**|**Object**|**Object**|**Object**|

 識別子に意味を持たない場合やパラメータ`value`の`item`型が重要でない場合✔️、型名を繰り返すのではなく、 or などの共通名を使用します。

## <a name="naming-new-versions-of-existing-apis"></a>既存の API の新しいバージョンの命名
 既存の API の新しいバージョンを作成するときに、古い API と同様の名前を使用✔️。

 これは、API 間の関係を強調するのに役立ちます。

 既存の API の新しいバージョンを示すプレフィックスではなくサフィックスを追加✔️。

 これは、ドキュメントを参照するとき、または IntelliSense を使用する場合の検出に役立ちます。 ほとんどのブラウザーと IntelliSense はアルファベット順に識別子を表示するため、API の古いバージョンは新しい API の近くに整理されます。

 ✔️、サフィックスやプレフィックスを追加するのではなく、新しいが意味のある識別子を使用することを検討してください。

 ✔️は、既存の API の新しいバージョンを示すために数値サフィックスを使用しますが、特に API の既存の名前が意味のある唯一の名前である場合 (つまり、業界標準である場合)、意味のあるサフィックスを追加する (または名前を変更する) ことが適切なオプションではない場合。

 ❌同じ API の以前のバージョンと区別するために、識別子に "Ex" (または類似の) サフィックスを使用しないでください。

 ✔️ DO は、32 ビット整数ではなく 64 ビット整数 (長整数) で動作する API のバージョンを導入する場合に、サフィックス 「64」を使用します。 既存の 32 ビット API が存在する場合にのみ、このアプローチを使用する必要があります。64 ビットバージョンの新しい API に対しては、この操作を行わないでください。

 *2005年&copy;、2009年マイクロソフト株式会社。すべての権利が予約されています。*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [命名のガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
- [EditorConfig での .NET の名前付け規則](/visualstudio/ide/editorconfig-naming-conventions)
