---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 19a70e500f6b75fd003bdb798f242cddb3926935
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964357"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
コンパイラが標準ライブラリを自動的に参照しないようにします。  
  
## <a name="syntax"></a>構文  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>Remarks  
 `-nostdlib`オプションを指定すると、System .dll アセンブリへの自動参照が削除され、コンパイラが vbc.exe ファイルを読み取ることができなくなります。 Vbc.exe ファイルと同じディレクトリにある vbc.exe ファイルは、一般的に使用される .NET Framework アセンブリを参照し、名前空間`System`と`Microsoft.VisualBasic`名前空間をインポートします。  
  
> [!NOTE]
> Mscorlib.dll および Microsoft の .dll アセンブリは常に参照されます。  
  
> [!NOTE]
> この`-nostdlib`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードは`T2.vb` 、標準ライブラリを参照せずにコンパイルされます。 オブジェクト`My`を削除する`_MYTYPE`には、条件付きコンパイル定数を文字列 "Empty" に設定する必要があります。  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>関連項目

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
