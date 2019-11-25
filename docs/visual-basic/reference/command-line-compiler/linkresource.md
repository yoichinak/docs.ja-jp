---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 0315645eccdc899ac9cf4d0be105297e1fa2a4c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335482"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
マネージド リソースへのリンクを作成します。  
  
## <a name="syntax"></a>構文  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

、または  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 必須です。 The resource file to link to the assembly. If the file name contains a space, enclose the name in quotation marks (" ").  
  
 `identifier`  
 省略可能です。 The logical name for the resource. The name that is used to load the resource. 既定値は、ファイルの名前です。 Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`. By default, `filename` is public in the assembly.  
  
## <a name="remarks"></a>Remarks  
 The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.  
  
 The `-linkresource` option requires one of the `-target` options other than `-target:module`.  
  
 If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace. (For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.  
  
 The file name can be any file format. たとえば、ネイティブ DLL をアセンブリの一部にすることで、グローバル アセンブリ キャッシュにインストールして、アセンブリ内のマネージド コードからアクセスできるようにすることができます。  
  
 `-linkresource` の省略形は `-linkres` です。  
  
> [!NOTE]
> The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.  
  
## <a name="example"></a>例  
 The following code compiles `in.vb` and links to resource file `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
