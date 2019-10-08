---
title: -リソース (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 5bedc346381f6de293933dce14a8c5c3044b246f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005197"
---
# <a name="-resource-visual-basic"></a>-リソース (Visual Basic)
マネージド リソースをアセンブリに埋め込みます。  
  
## <a name="syntax"></a>構文  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

または  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引数  
  
|項目|定義|  
|---|---|  
|`filename`|必須。 出力ファイルに埋め込むリソースファイルの名前。 既定では、`filename` はアセンブリ内で公開されています。 ファイル名にスペースが含まれている場合は、ファイル名を引用符 ("") で囲みます。|  
|`identifier`|任意。 リソースの論理名。読み込みに使用される名前。 既定値は、ファイルの名前です。 必要に応じて、次のように、アセンブリマニフェストでリソースがパブリックであるかプライベートであるかを指定できます。 `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>コメント  
 リソースファイルを出力ファイルに配置せずにリソースをアセンブリにリンクするには、`-linkresource` を使用します。  
  
 @No__t-0 が[resgen.exe (リソースファイルジェネレーター)](../../../framework/tools/resgen-exe-resource-file-generator.md)や開発環境などで作成された .NET Framework のリソースファイルである場合、<xref:System.Resources> 名前空間のメンバーを使用してアクセスできます (詳細については、「@no__t」を参照してください)。 実行時に他のすべてのリソースにアクセスするには、次のいずれかの方法を使用します。 <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>、<xref:System.Reflection.Assembly.GetManifestResourceNames%2A>、または <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>。  
  
 `-resource` の省略形は `-res` です。  
  
 Visual Studio IDE で `-resource` を設定する方法の詳細については、「[アプリケーションリソースの管理 (.net)](/visualstudio/ide/managing-application-resources-dotnet)」を参照してください。  
  
## <a name="example"></a>例  
 次のコードは `In.vb` をコンパイルし、リソースファイルをアタッチ `Rf.resource` です。  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
