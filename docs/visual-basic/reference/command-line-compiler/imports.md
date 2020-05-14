---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 2a1dd19189ff65413255b9bc137e1a7f0227bbe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716648"
---
# <a name="-imports-visual-basic"></a>-imports (Visual Basic)
指定されたアセンブリから名前空間をインポートします。  
  
## <a name="syntax"></a>構文  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`namespaceList`|必須です。 インポートされる名前空間のコンマ区切りの一覧。|  
  
## <a name="remarks"></a>Remarks  
 `-imports` オプションでは、参照アセンブリから、あるいはソース ファイルの現在のセット内に定義されている名前空間をインポートします。  
  
 `-imports` で指定された名前空間のメンバーは、コンパイル時にすべてのソースコード ファイルで使用できます。 単一のソースコード ファイルで名前空間を使用するには、[ ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) を使用します。  
  
|Visual Studio 統合開発環境で -imports を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2. **[参照]** タブをクリックします。<br />3. **[ユーザー インポートの追加]** ボタンの横にあるボックスに、名前空間の名前を入力します。<br />4. **[ユーザー インポートの追加]** ボタンをクリックします。|  
  
## <a name="example"></a>例  
 `-imports:system.globalization` が指定されている場合、次のコードがコンパイルされます。 それがない場合、正常にコンパイルするには、ソース コード ファイルの先頭に `Imports System.Globalization` ステートメントを含めるか、プロパティを `System.Globalization.CultureInfo.CurrentCulture.Name` として完全に修飾する必要があります。

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
