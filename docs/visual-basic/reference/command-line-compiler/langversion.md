---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: db2cb1eb107973e9ce60ecb0d669c677d4fa2c51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793958"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
コンパイラで指定された Visual Basic 言語のバージョンに含まれている構文のみを受け入れるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a>引数  
 `version`  
 必須。 コンパイル時に使用する言語バージョン。 許容値は`9`、 `10`、 `11`、 `12`、 `14`、 `15`、 `15.3`、 `15.5`、`default`と`latest`します。

 整数のいずれかを指定するとを使用して`.0`マイナー バージョンとして`11.0`します。

 指定することで、使用可能なすべての値の一覧を表示できます`-langversion:?`コマンド行にします。  
  
## <a name="remarks"></a>Remarks  
 `-langversion`オプションは、コンパイラはどのような構文を指定します。 たとえば、言語バージョンが 9.0 であることを指定する場合、コンパイラは、バージョン 10.0 でのみ有効であり、以降は、構文エラーを生成します。  
  
 .NET Framework の異なるバージョンを対象アプリケーションを開発する際に、このオプションを使用することができます。 たとえば、.NET Framework 3.5 をターゲットにする場合は、言語バージョン 10.0 から構文を使用しないようにする、このオプションを使用できます。  
  
 設定できる`-langversion`直接、コマンドラインを使用してのみです。 詳細については、「[対象となる特定の .NET Framework のバージョンの指定](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)」を参照してください。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`sample.vb`Visual Basic 9.0 の。  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [対象となる特定の .NET Framework バージョンの指定](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
