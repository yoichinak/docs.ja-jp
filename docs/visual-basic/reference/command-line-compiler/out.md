---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 67366e13e4dceea4772d0730222413cb25b4e8b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352390"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
出力ファイルの名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`filename`|必須です。 The name of the output file the compiler creates. If the file name contains a space, enclose the name in quotation marks (" ").|  
  
## <a name="remarks"></a>Remarks  
 Specify the full name and extension of the file to create. If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.  
  
 If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.  
  
|To set -out in the Visual Studio integrated development environment|  
|---|  
|1.  Have a project selected in **Solution Explorer**. **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.  Click the **Application** tab.<br />3.  Modify the value in the **Assembly Name** box.|  
  
## <a name="example"></a>例  
 The following code compiles `T2.vb` and creates output file `T2.exe`.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
