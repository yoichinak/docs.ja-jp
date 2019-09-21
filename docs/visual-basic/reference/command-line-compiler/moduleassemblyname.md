---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: dc4c0336c8a67a1b4e70f71ba5f5406da1fbb2ff
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972374"
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
|`assembly_name`|このモジュールが含まれるアセンブリの名前。|  
  
## <a name="remarks"></a>Remarks  
 オプションが指定さ`-moduleassemblyname`れて`-target:module`いる場合にのみ、コンパイラはオプションを処理します。 これにより、コンパイラによってモジュールが作成されます。 コンパイラによって作成されたモジュールは、 `-moduleassemblyname`オプションで指定されたアセンブリに対してのみ有効です。 モジュールを別のアセンブリに配置すると、実行時エラーが発生します。  
  
 `-moduleassemblyname`オプションは、次の条件に該当する場合にのみ必要です。  
  
- モジュール内のデータ型は、参照され`Friend`たアセンブリの型にアクセスする必要があります。  
  
- 参照アセンブリは、モジュールがビルドされるアセンブリへのフレンドアセンブリアクセスを許可されています。  
  
 モジュールの作成の詳細については、「 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)」を参照してください。 フレンドアセンブリの詳細については、「[フレンドアセンブリ](../../../standard/assembly/friend.md)」を参照してください。  
  
> [!NOTE]
> この`-moduleassemblyname`オプションは、Visual Studio 開発環境内からは使用できません。コマンドプロンプトからコンパイルする場合にのみ使用できます。  
  
## <a name="see-also"></a>関連項目

- [方法: マルチファイル アセンブリをビルドする](../../../framework/app-domains/build-multifile-assembly.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [フレンド アセンブリ](../../../standard/assembly/friend.md)
