---
title: XML ドキュメント (F#)
description: コメントからドキュメントを生成するためには、F# でのサポートについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: c5305dea8832112644710b2863269ef00feddd10
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204679"
---
# <a name="xml-documentation"></a>XML に関するドキュメント

トリプル スラッシュ (///) からドキュメントを生成するコードで F# コメント。 XML コメントには、コード ファイル (.fs) や署名 (.fsi) ファイル内の宣言が前に記述できます。

## <a name="generating-documentation-from-comments"></a>コメントからドキュメントを生成します。

サポートF#他の .NET Framework 言語ではコメントからドキュメントを生成すると同じです。 その他の .NET Framework 言語では、ように、 [-doc コンパイラ オプション](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)などのツールを使用して、ドキュメントに変換できる情報を含む XML ファイルを作成することができます[DocFX](https://dotnet.github.io/docfx/)または[Sandcastle](https://github.com/EWSoftware/SHFB)します。 一般に他の .NET Framework 言語で記述されているアセンブリで使用するために設計されたツールを使用して、生成されたドキュメントでは、F# の構成要素のコンパイル済みの形式に基づいている Api のビューを生成します。 ツール具体的には F# をサポートしない限り、これらのツールによって生成されたドキュメントは API の F# ビューと一致しません。

XML ドキュメントを生成する方法の詳細については、[XML ドキュメント コメント&#40;C&#35;プログラミング ガイド&#41;](https://msdn.microsoft.com/library/b2s063f7)を参照してください。

## <a name="recommended-tags"></a>推奨されるタグ

XML ドキュメント コメントを記述する 2 つの方法はあります。 1 つに、XML タグを使用せず、トリプル スラッシュ コメントで直接、ドキュメントを書き込むだけです。 これを行う場合は、コメント テキスト全体が直後に続くコード コンス トラクターの概要のドキュメントとして扱われます。 各構成要素の概要を記述する場合は、このメソッドを使用します。 その他のメソッドでは、XML タグを使用してより構造化ドキュメントを提供します。 2 番目のメソッドでは、簡単な概要、詳細説明、各パラメーターと型パラメーターと例外がスローされると、ドキュメント、および戻り値の説明を個別に指定することができます。 次の表に、XML タグで認識されるF#XML コード コメント。

|タグ構文|説明|
|----------|-----------|
|**\<c\>**_text_**\</c\>**|指定します*テキスト*コードに示します。 このタグは、コードの適切なフォントでテキストを表示するドキュメント ジェネレーターによって使用できます。|
|**\<summary\>**_text_**\</summary\>**|指定します*テキスト*プログラム要素の簡単な説明です。 説明は、通常は 1 ~ 2 文です。|
|**\<「解説」\>**_テキスト_**\</remarks\>**|指定します*テキスト*プログラム要素に関する補足情報が含まれています。|
|**\<param name="**_name_**"\>**_description_**\</param\>**|関数またはメソッド パラメーターの説明と名前を指定します。|
|**\<typeparam name="**_name_**"\>**_description_**\</typeparam\>**|型パラメーターの説明と名前を指定します。|
|**\<返します\>**_テキスト_**\</returns\>**|指定します*テキスト*関数またはメソッドの戻り値について説明します。|
|**\<exception cref="**_type_**"\>**_description_**\</exception\>**|生成できる例外がスローされた状況の種類を指定します。|
|**\<see cref="**_reference_**"\>**_text_**\</see\>**|別のプログラム要素へのインライン リンクを指定します。 *参照*は、XML ドキュメント ファイルに表示される名前。 *テキスト*はリンクに表示されるテキスト。|
|**\<seealso cref="**_reference_**"/\>**|別の種類のドキュメントへの参照リンクを指定します。 *参照*は、XML ドキュメント ファイルに表示される名前。 ドキュメント ページの下部に表示される通常のリンクを参照してください。|
|**\<para\>**_テキスト_**\</para\>**|段落のテキストを指定します。 これには、使用中のテキストを分離する、**解説**タグ。|

## <a name="example"></a>例

### <a name="description"></a>説明

シグネチャ ファイルでは、一般的な XML ドキュメント コメントを次に示します。

### <a name="code"></a>コード

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>例

### <a name="description"></a>説明

次の例では、XML タグのない別の方法を示します。 この例では、コメント内のテキスト全体が概要と見なされます。 Summary タグを明示的に指定しない場合は、指定することする必要がありますいないその他のタグなど**param**または**返します**タグ。

### <a name="code"></a>コード

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [コンパイラ オプション](compiler-options.md)
