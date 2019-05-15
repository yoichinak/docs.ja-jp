---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 637a1d4b7a523feb2fc8da10a0c18e68774c480a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586689"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
マネージド リソースへのリンクを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 必須。 アセンブリにリンクするリソース ファイル。 ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("")。  
  
 `identifier`  
 省略可能です。 リソースの論理名。 リソースの読み込みに使用される名前です。 既定値は、ファイルの名前です。 かどうか、ファイルがパブリックかプライベート アセンブリ マニフェストの例を指定する必要に応じて、:`-linkres:filename.res,myname.res,public`します。 既定では、`filename`アセンブリ内でパブリックです。  
  
## <a name="remarks"></a>Remarks  
 `-linkresource`オプションは、リソース ファイルを出力ファイルに埋め込まれません。 を使用して、`-resource`これを実行するオプション。  
  
 `-linkresource`オプションでは、いずれかが必要です、`-target`以外のオプション`-target:module`します。  
  
 場合`filename`作成例についてでの .NET Framework リソース ファイルには、 [Resgen.exe (リソース ファイル ジェネレーター)](../../../framework/tools/resgen-exe-resource-file-generator.md)または開発環境でアクセスできるメンバー間で、<xref:System.Resources>名前空間。 (詳細については、「<xref:System.Resources.ResourceManager>」を参照してください)。実行時にその他のすべてのリソースにアクセスするで始まるメソッドを使用して`GetManifestResource`で、<xref:System.Reflection.Assembly>クラス。  
  
 ファイル名には、任意のファイル形式を指定できます。 たとえば、ネイティブ DLL をアセンブリの一部にすることで、グローバル アセンブリ キャッシュにインストールして、アセンブリ内のマネージド コードからアクセスできるようにすることができます。  
  
 `-linkresource` の省略形は `-linkres` です。  
  
> [!NOTE]
>  `-linkresource`オプションは、Visual Studio 開発環境から使用できません。 コマンドラインからコンパイルするときにのみ、は使用できます。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`in.vb`とリソース ファイルへのリンク`rf.resource`します。  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-リソース (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
