---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 5b26e36346858d95526f5d5ce7d4645bea1dbe05
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005480"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
このモジュールが一部となるアセンブリの名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>引数  
  
|項目|定義|  
|---|---|  
|`assembly_name`|このモジュールが含まれるアセンブリの名前。|  
  
## <a name="remarks"></a>コメント  
 コンパイラは、`-target:module` オプションが指定されている場合にのみ、`-moduleassemblyname` オプションを処理します。 これにより、コンパイラによってモジュールが作成されます。 コンパイラによって作成されたモジュールは、`-moduleassemblyname` オプションで指定されたアセンブリに対してのみ有効です。 モジュールを別のアセンブリに配置すると、実行時エラーが発生します。  
  
 @No__t-0 オプションは、次の条件に該当する場合にのみ必要です。  
  
- モジュール内のデータ型は、参照されたアセンブリの @no__t 0 型にアクセスする必要があります。  
  
- 参照アセンブリは、モジュールがビルドされるアセンブリへのフレンドアセンブリアクセスを許可されています。  
  
 モジュールの作成の詳細については、「 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)」を参照してください。 フレンドアセンブリの詳細については、「[フレンドアセンブリ](../../../standard/assembly/friend.md)」を参照してください。  
  
> [!NOTE]
> @No__t-0 オプションは、Visual Studio 開発環境内からは使用できません。これは、コマンドプロンプトからコンパイルする場合にのみ使用できます。  
  
## <a name="see-also"></a>関連項目

- [2 つのオブジェクトが等しいかどうかをテストする方法マルチファイル アセンブリをビルドする](../../../framework/app-domains/build-multifile-assembly.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [フレンド アセンブリ](../../../standard/assembly/friend.md)
