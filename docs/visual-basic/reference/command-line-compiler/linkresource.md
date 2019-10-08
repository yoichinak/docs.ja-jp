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
ms.openlocfilehash: dee5384696d543442f3280b9fdb535a7d9b6f863
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005489"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
マネージド リソースへのリンクを作成します。  
  
## <a name="syntax"></a>構文  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

または  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 必須。 アセンブリにリンクするリソースファイル。 ファイル名にスペースが含まれている場合は、名前を引用符 ("") で囲みます。  
  
 `identifier`  
 任意。 リソースの論理名。 リソースの読み込みに使用される名前。 既定値は、ファイルの名前です。 必要に応じて、ファイルがアセンブリマニフェスト内でパブリックであるかプライベートであるかを指定できます。たとえば、`-linkres:filename.res,myname.res,public` です。 既定では、`filename` はアセンブリ内で公開されています。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 オプションでは、リソースファイルは出力ファイルに埋め込まれません。これを行うには、`-resource` オプションを使用します。  
  
 @No__t-0 オプションには、`-target:module` 以外の `-target` オプションのいずれかが必要です。  
  
 @No__t-0 は、 [resgen.exe (リソースファイルジェネレーター)](../../../framework/tools/resgen-exe-resource-file-generator.md)や開発環境などで作成された .NET Framework のリソースファイルである場合、<xref:System.Resources> 名前空間のメンバーを使用してアクセスできます。 (詳細については、「<xref:System.Resources.ResourceManager>」を参照してください)。実行時に他のすべてのリソースにアクセスするには、<xref:System.Reflection.Assembly> クラスの `GetManifestResource` で始まるメソッドを使用します。  
  
 ファイル名には任意のファイル形式を使用できます。 たとえば、ネイティブ DLL をアセンブリの一部にすることで、グローバル アセンブリ キャッシュにインストールして、アセンブリ内のマネージド コードからアクセスできるようにすることができます。  
  
 `-linkresource` の省略形は `-linkres` です。  
  
> [!NOTE]
> @No__t-0 オプションは、Visual Studio 開発環境では使用できません。これは、コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードは `in.vb` をコンパイルし、リソースファイル `rf.resource` にリンクします。  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-リソース (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
