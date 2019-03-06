---
title: -langversion (C# コンパイラ オプション)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 19d7f20bf33de6e23860d475f38d49553049dec1
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211963"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (C# コンパイラ オプション)

コンパイラが、選択した C# 言語仕様に含まれている構文のみを受け入れるようにします。  
  
## <a name="syntax"></a>構文  

```console
-langversion:option  
```

## <a name="arguments"></a>引数

 `option`  
 有効な値は、次のとおりです。  
  
|オプション|説明|  
|------------|-------------|  
|preview|コンパイラは、サポート可能な最新のプレビュー バージョンの有効な言語構文をすべて受け入れます。|
|latest|コンパイラは、サポート可能な最新バージョン (マイナー リリースを含む) の有効な言語構文をすべて受け入れます。|
|latestMajor|コンパイラは、最新のメジャー バージョンからサポートできるすべての有効な言語構文を受け入れます。|
|8.0|コンパイラは、C# 8.0 以下に含まれている構文のみを受け入れます。 <sup id="TCS80">[CS80](#FCS80)</sup>|
|7.3|コンパイラは、C# 7.3 以下に含まれている構文のみを受け入れます<sup id="TCS73">[CS73](#FCS73)</sup>|
|7.2|コンパイラは、C# 7.2 以下に含まれている構文のみを受け入れます<sup id="TCS72">[CS72](#FCS72)</sup>|
|7.1|コンパイラは、C# 7.1 以下に含まれている構文のみを受け入れます<sup id="TCS71">[CS71](#FCS71)</sup>|
|7|コンパイラは、C# 7.0 以下に含まれている構文のみを受け入れます<sup id="TCS7">[CS7](#FCS7)</sup>|
|6|コンパイラは、C# 6.0 以下に含まれている構文のみを受け入れます<sup id="TCS6">[CS6](#FCS6)</sup>|
|5|コンパイラは、C# 5.0 以下に含まれている構文のみを受け入れます<sup id="TCS5">[CS5](#FCS5)</sup>|
|4|コンパイラは、C# 4.0 以下に含まれている構文のみを受け入れます<sup id="TCS4">[CS4](#FCS4)</sup>|
|3|コンパイラは、C# 3.0 以下に含まれている構文のみを受け入れます<sup id="TCS3">[CS3](#FCS3)</sup>|
|ISO-2|コンパイラは、ISO/IEC 23270:2006 C# (2.0) に含まれている構文のみを受け入れます<sup id="TISO2">[ISO2](#FISO2)</sup>|
|ISO-1|コンパイラは、ISO/IEC 23270:2003 C# (1.0/1.2) に含まれている構文のみを受け入れます<sup id="TISO1">[ISO1](#FISO1)</sup>|  

## <a name="remarks"></a>解説

 C# アプリケーションで参照されるメタデータは、**-langversion** コンパイラ オプションの対象になりません。  
  
 C# コンパイラのバージョンごとに言語仕様の拡張機能が含まれているため、**-langversion** は、コンパイラの以前のバージョンと同じ機能を提供しません。  

 さらに、C# バージョンの更新は、一般的に主要な .NET Framework のリリースと一致しますが、新しい構文および機能は必ずしも特定のフレームワーク バージョンに関連付けられていません。 新機能では、C# リビジョンと共にリリースされる新しいコンパイラの更新プログラムを確実に必要としますが、各特定機能には、独自の最小の .NET API または共通言語ランタイムの要件があり、この要件によって、NuGet パッケージやその他のライブラリを含めることで下位レベルのフレームワークで実行できるようになります。
  
 使用する **-langversion** の設定に関係なく、現在のバージョンの共通言語ランタイムを使用して .exe や .dll を作成します。 1 つの例外は、**-langversion:ISO-1** の下で機能する、フレンド アセンブリと [-moduleassemblyname (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) です。  

 C# 言語バージョンを指定するその他の方法については、「[C# 言語のバージョンの選択](../configure-language-version.md)」のトピックを参照してください。
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>」を参照してください。  

## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)

### <a name="c-language-specification"></a>C# 言語仕様

|Version|リンク|説明|
|-------|----|-----------|
|C# 7.0 以降||現在使用できません|
|C# 6.0|[リンク](../language-specification/index.md)|C# 言語仕様バージョン 6 - 非公式ドラフト: .NET Foundation|
|C# 5.0|[PDF のダウンロード](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Standard ECMA-334 5th Edition|
|C# 3.0|[DOC のダウンロード](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C# 言語仕様バージョン 3.0:Microsoft Corporation|
|C# 2.0|[PDF のダウンロード](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Standard ECMA-334 4th Edition|
|C# 1.2|[DOC のダウンロード](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C# 言語仕様バージョン 1.2:Microsoft Corporation|
|C# 1.0|[DOC のダウンロード](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C# 言語仕様バージョン 1.0:Microsoft Corporation|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>すべての言語機能をサポートするために必要な最小コンパイラ バージョン

[↩](#TCS80)<a name="FCS80">CS80</a>:Microsoft Visual Studio/Build Tools 2019、バージョン 16、または .NET Core 3.0 SDK [↩](#TCS73)<a name="FCS73">CS73</a>:Microsoft Visual Studio/Build Tools 2017、バージョン 15.7  
[↩](#TCS72)<a name="FCS72">CS72</a>:Microsoft Visual Studio/Build Tools 2017、バージョン 15.5  
[↩](#TCS71)<a name="FCS71">CS71</a>:Microsoft Visual Studio/Build Tools 2017、バージョン 15.3  
[↩](#TCS7)<a name="FCS7">CS7</a>:Microsoft Visual Studio/Build Tools 2017  
[↩](#TCS6)<a name="FCS6">CS6</a>:Microsoft Visual Studio/Build Tools 2015  
[↩](#TCS5)<a name="FCS5">CS5</a>:Microsoft Visual Studio/Build Tools 2012、またはバンドルされている .Net Framework 4.5 コンパイラ  
[↩](#TCS4)<a name="FCS4">CS4</a>:Microsoft Visual Studio/Build Tools 2010、またはバンドルされている .Net Framework 4.0 コンパイラ  
[↩](#TCS3)<a name="FCS3">CS3</a>:Microsoft Visual Studio/Build Tools 2008、またはバンドルされている .Net Framework 3.5 コンパイラ  
[↩](#TISO2)<a name="FISO2">ISO2</a>:Microsoft Visual Studio/Build Tools 2005、またはバンドルされている .Net Framework 2.0 コンパイラ  
[↩](#TISO1)<a name="FISO1">ISO1</a>:Microsoft Visual Studio/Build Tools .Net 2002、またはバンドルされている .Net Framework 1.0 コンパイラ  
