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
author: KrzysztofCwalina
ms.openlocfilehash: ae1b7ce83f6698cef470aabf07a12d89042ab8a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667688"
---
# <a name="general-naming-conventions"></a>一般的な名前付け規則
このセクションでは、一般的な名前付け規則、単語の選択に関連する言語固有の名前を使用しないようにする方法の省略形と頭字語、および推奨事項の使用に関するガイドラインについて説明します。  
  
## <a name="word-choice"></a>単語の選択  
 **✓ DO** 読みやすい識別子の名前を選択します。  
  
たとえば、`AlighmentHorizontal`よりも英語読みしやすい `HorizontalAlighment`という名前を選択します。
  
 **✓ DO** 簡潔さよりも読みやすさを優先します。  
  
 プロパティ名として（Ｘ軸というのがわかりにくい）`ScrollableX` よりも `CanScrollHorizontally` の方が良いです。  
  
 **× DO NOT** アンダー スコア、ハイフン、またはその他の英数字以外の文字は使用しないでください。 
  
 **× DO NOT** ハンガリアン記法を使用しないでください。
  
 **× AVOID** 広く使用されているプログラミング言語のキーワードと競合する識別子の使用を避けます。
  
 共通言語仕様（CLS）に準拠している言語は、ルール4に従って、その言語のキーワードを識別子名として使用する名前付けされた項目へのアクセスを許す機構を供給しなくてはなりません。 たとえば C# の場合、@ 記号をエスケープ メカニズムとして使用します。しかしながら、エスケープ シーケンスを使う方法は、それを使わない方法よりもずっと難しいので、共通のキーワードを避けることをお勧めします。 
  
## <a name="using-abbreviations-and-acronyms"></a>省略形と頭字語を使用します。  
 **× DO NOT** 識別子名の一部としての省略形または短縮形を使用ないでください。 
  
 たとえば、`GetWin` ではなく、`GetWindow` を使用します。

**x DO NOT** 広く受け入れられていない頭字語は使用しないでください。使用する場合は、必要な場合にのみにしてください。

 必要である時だけ、頭文字を使用します。広く受け入れられていない頭文字は使用しません。   

## <a name="avoiding-language-specific-names"></a>言語固有の名前を回避します。  
 **✓ DO** 型名に言語固有のキーワードではなく、意味的にわかりやすい名前を使用します。  
  
 たとえば、`GetInt` よりも `GetLength`を使用します。  
  
 **✓ DO** 識別子名が、その型以外の意味がないまれな場合には、言語固有の名称ではなく、汎用の CLR 型名を使用します。  
  
 たとえば、<xref:System.Int64>へ変換するメソッドは、`ToLong` ではなく `toInt64` という名前を付けます (<xref:System.Int64> は、C# 固有の `long`の CLR 名です-特定のエイリアス`long`)。 次の表は、CLR 型名 (だけでなく C#、Visual Basic、および C++ の対応する型名) を使用していくつかの基本データ型を示します。
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**unsigned char**|**Byte**|  
|**short**|**Short**|**short**|**Int16**|  
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|  
|**int**|**Integer**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|  
|**float**|**Single**|**float**|**Single**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**Boolean**|**bool**|**Boolean**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**String**|**String**|**String**|  
|**object**|**Object**|**Object**|**Object**|  
  
 **✓ DO** 名前が意味を持たず、パラメーターの型が重要ではないまれな場合は、型名を繰り返すのではなく、`value` または `item` などの共通名を使用します。 
  
## <a name="naming-new-versions-of-existing-apis"></a>既存の Api の新しいバージョンの名前を付ける  
 **✓ DO** 既存の API の新しいバージョンを示すには、プレフィックスではなく、サフィックスを追加します。
  
 これにより、API の間の関係性を強調します。  
  
 **✓ DO** 既存の API の新しいバージョンを示す接頭辞ではなく、サフィックスを追加します。 
  
 これは、ドキュメントを参照したり、IntelliSense を使用したりする際に発見しやすくなります。 ほとんどのブラウザーや IntelliSense は、アルファベット順に名前を並べるため、新しいバージョンの API は、古いバージョンの API の近くに編成されます。
  
 **✓ CONSIDER** サフィックスまたはプリフィックスを追加する代わりに、新しく意味のある識別子を使用します。  
  
 **✓ DO** もし、既存の API の名前が意味をなす唯一の名前であって（すなわち、それが規格や標準によるものであり）、意味のあるサフィックスを加えること（あるいは新しい名前を付けること）が適切ではないなら、既存の API の新しいバージョンであることを、数字のサフィックスを使って表します。  
  
 **X DO NOT** 同じ API の以前のバージョンと区別するために、"Ex"(または類似した) サフィックスを使用して識別子を作ります。  
  
 **✓ DO** 32 ビット整数の代わりに 64 ビット整数 (長整数) で動作する API のバージョンを導入するときに、**「64」サフィックス**を使用します。 既存の 32 ビット API が存在する場合にのみ、この方法を実行する必要があります。64 ビット バージョンのみの新しい API には使用しないでください。
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
