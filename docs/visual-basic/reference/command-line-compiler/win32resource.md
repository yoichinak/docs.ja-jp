---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 382dcc6571aa06ecdfc32bf43080c4b7a36eb1f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961298"
---
# <a name="-win32resource"></a>-win32resource
Win32 リソースファイルを出力ファイルに挿入します。  
  
## <a name="syntax"></a>構文  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 出力ファイルに追加するリソースファイルの名前。 ファイル名にスペースが含まれている場合は、ファイル名を引用符 ("") で囲みます。  
  
## <a name="remarks"></a>Remarks  
 Win32 リソースファイルは、Microsoft Windows リソースコンパイラ (RC) を使用して作成できます。  
  
 Win32 リソースには、**ファイルエクスプローラー**でアプリケーションを識別するのに役立つバージョンまたはビットマップ (アイコン) 情報を含めることができます。 を指定`-win32resource`しない場合、コンパイラはアセンブリのバージョンに基づいてバージョン情報を生成します。 オプション`-win32resource` と`-win32icon`オプションは同時に指定できません。  
  
 .NET Framework リソースファイルを参照する場合は[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)を参照し、.NET Framework リソースファイルをアタッチする場合は[-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)を参照してください。  
  
> [!NOTE]
> この`-win32resource`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードは`In.vb` 、Win32 リソースファイルを`Rf.res`コンパイルしてアタッチします。  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
