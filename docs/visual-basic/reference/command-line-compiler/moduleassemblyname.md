---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 70cef109e4f2947fb4e38b9bfd19433257cce136
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663506"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
このモジュールが一部となるアセンブリの名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`assembly_name`|このモジュールの一部となるアセンブリの名前。|  
  
## <a name="remarks"></a>Remarks  
 コンパイラ プロセス、`-moduleassemblyname`オプション場合にのみ、`-target:module`オプションが指定されました。 これにより、コンパイラでモジュールを作成します。 コンパイラによって作成されたモジュールがで指定されたアセンブリに対してのみ有効ですが、`-moduleassemblyname`オプション。 別のアセンブリでモジュールを配置する場合は、実行時エラーが発生します。  
  
 `-moduleassemblyname`オプションは、次に該当する場合にのみ必要があります。  
  
- モジュール内のデータ型へのアクセスを必要な`Friend`参照先アセンブリの型。  
  
- 参照アセンブリがモジュールをビルドするアセンブリにフレンド アセンブリのアクセスを付与します。  
  
 モジュールの作成方法の詳細については、次を参照してください。 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)します。 フレンド アセンブリの詳細については、次を参照してください。[フレンド アセンブリ](../../../standard/assembly/friend-assemblies.md)します。  
  
> [!NOTE]
>  `-moduleassemblyname`オプションは、Visual Studio 開発環境内からは使用できません。 コマンド プロンプトからコンパイルするときにのみ、は使用できます。  
  
## <a name="see-also"></a>関連項目

- [方法: マルチファイル アセンブリをビルドする](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-参照 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [フレンド アセンブリ](../../../standard/assembly/friend-assemblies.md)
