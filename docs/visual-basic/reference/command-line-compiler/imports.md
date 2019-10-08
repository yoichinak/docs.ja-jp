---
title: -imports (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 929e24a1ffd02d4e21ab1b925ddd59050b5d3cc4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005564"
---
# <a name="-imports-visual-basic"></a>-imports (Visual Basic)
指定したアセンブリから名前空間をインポートします。  
  
## <a name="syntax"></a>構文  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>引数  
  
|項目|定義|  
|---|---|  
|`namespaceList`|必須。 インポートする名前空間のコンマ区切りの一覧。|  
  
## <a name="remarks"></a>コメント  
 @No__t-0 オプションは、ソースファイルの現在のセットまたは参照されているアセンブリの中で定義されているすべての名前空間をインポートします。  
  
 @No__t-0 で指定された名前空間のメンバーは、コンパイル時にすべてのソースコードファイルで使用できます。 [Imports ステートメント (.Net 名前空間と型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)を使用して、1つのソースコードファイルで名前空間を使用します。  
  
|Visual Studio 統合開発環境で/imports を設定するには|  
|---|  
|1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2. **[参照]** タブをクリックします。<br />3. **[ユーザーインポートの追加]** ボタンの横にあるボックスに、名前空間の名前を入力します。<br />4。 **[ユーザーインポートの追加]** ボタンをクリックします。|  
  
## <a name="example"></a>例  
 @No__t-0 を指定すると、次のコードがコンパイルされます。 それがない場合、コンパイルが成功するには、ソースコードファイルの先頭に @no__t 0 ステートメントが含まれているか、プロパティが `System.Globalization.CultureInfo.CurrentCulture.Name` として完全に修飾されている必要があります。

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
