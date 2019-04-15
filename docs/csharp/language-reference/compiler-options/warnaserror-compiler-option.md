---
title: -warnaserror (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 2ae555c2e049e687f508e62b5b46fd8a744e827f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329104"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (C# コンパイラ オプション)
**-warnaserror+** オプションは、すべての警告をエラーとして扱います  
  
## <a name="syntax"></a>構文  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>解説  
 通常は警告として報告されるすべてのメッセージが、代わりにエラーとして報告され、ビルド プロセスが停止します (出力ファイルはビルドされません)。  
  
 既定では、**-warnaserror-** が有効になっているため、警告により出力ファイルの生成が妨げられることはありません。 **-warnaserror** は **-warnaserror+** と同じで、警告がエラーとして扱われます。  
  
 必要に応じて、いくつかの特定の警告のみをエラーとして扱う場合は、エラーとして扱う警告番号のコンマ区切りのリストを指定できます。  
  
 コンパイラで表示する警告のレベルを指定するには、[-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) を使用します。 特定の警告を無効にするには、[-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) を使用します。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1. プロジェクトの **[プロパティ]** ページを開きます。  
  
2. **[ビルド]** プロパティ ページをクリックします。  
  
3. **警告をエラーとして扱う**プロパティを変更します。  
  
 このコンパイラ オプションをプログラムによって設定するには、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>」を参照してください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルして、コンパイラで警告を表示させないようにします。  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
