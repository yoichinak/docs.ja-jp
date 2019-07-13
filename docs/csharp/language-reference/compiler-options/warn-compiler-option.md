---
title: -warn (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 17dd992edbec5ce444b53ed42b2b486282618672
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59315804"
---
# <a name="-warn-c-compiler-options"></a>-warn (C# コンパイラ オプション)
**-warn** オプションは、コンパイラが表示する警告レベルを指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>引数  
 `option`  
 コンパイルで表示する警告レベル:数値が小さいほど重要度が高い警告のみが表示され、数値が大きいほど多くの警告が表示されます。 有効な値は 0 から 4 です。  
  
|警告レベル|説明|  
|-------------------|-------------|  
|0|すべての警告メッセージの出力をオフにします。|  
|1|重大な警告メッセージを表示します。|  
|2|レベル 1 の警告に加え、クラス メンバーの非表示に関する警告など、より重大度の低い特定の警告を表示します。|  
|3|レベル 2 の警告に加え、常に `true` または `false` に評価される式に関する警告など、より重大度の低い特定の警告を表示します。|  
|4 (既定)|レベルの 3 の警告に加え、情報のための警告を表示します。|  
  
## <a name="remarks"></a>解説  
 エラーまたは警告に関する情報を取得するには、ヘルプの索引でエラー コードを検索することができます。 エラーまたは警告に関する情報を取得する他の方法については、「[C# コンパイラ エラー](../../../csharp/language-reference/compiler-messages/index.md)」を参照してください。  
  
 すべての警告をエラーとして扱う場合は [-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) を使用します。 特定の警告を無効にするには、[-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) を使用します。  
  
 **-w** は **-warn** の省略形です。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1. プロジェクトの **[プロパティ]** ページを開きます。  
  
2. **[ビルド]** プロパティ ページをクリックします。  
  
3. **警告レベル** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルして、コンパイラにレベル 1 の警告のみを表示させます。  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
