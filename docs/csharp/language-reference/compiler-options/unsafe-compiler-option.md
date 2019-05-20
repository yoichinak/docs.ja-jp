---
title: -unsafe (C# コンパイラ オプション)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877988"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (C# コンパイラ オプション)

**-unsafe** コンパイラ オプションは、[unsafe](../keywords/unsafe.md) キーワードを使用するコードをコンパイルできるようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>解説

アンセーフ コードの詳細については、「[アンセーフ コードとポインター](../../programming-guide/unsafe-code-pointers/index.md)」を参照してください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1. プロジェクトの **[プロパティ]** ページを開きます。  
  
2. **[ビルド]** プロパティ ページをクリックします。  
  
3. **[アンセーフ コードの許可]** チェック ボックスをオンにします。  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>このオプションを csproj ファイルに追加するには

プロジェクトの .csproj ファイルを開き、次の要素を追加します。

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>」を参照してください。  
  
## <a name="example"></a>例

unsafe モードで `in.cs` をコンパイルする場合は、次のコードを使用します。  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
