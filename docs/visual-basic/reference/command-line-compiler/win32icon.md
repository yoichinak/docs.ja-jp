---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: dc48a8f79aa04892c514917da00b8fd6489695b1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593086"
---
# <a name="-win32icon"></a>-win32icon
.Ico ファイルを出力ファイルに挿入します。 この .ico ファイルは、出力ファイルを表す**ファイル エクスプ ローラー**します。  
  
## <a name="syntax"></a>構文  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`filename`|出力ファイルに追加する .ico ファイル。 ファイル名を引用符で囲みます ("")、スペースが含まれている場合。|  
  
## <a name="remarks"></a>Remarks  
 .Ico ファイルは、Microsoft Windows リソース コンパイラ (RC) を作成できます。 リソース コンパイラが、Visual C プログラムをコンパイルするときに呼び出されます.ico ファイルは .rc ファイルから作成されます。 `-win32icon`と`-win32resource`オプションは相互に排他的です。  
  
 参照してください[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) 、.NET Framework リソース ファイルを参照または[-リソース (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) .NET Framework リソース ファイルを添付します。 参照してください[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res ファイルをインポートします。  
  
|Visual Studio IDE で win32icon を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[アプリケーション]** タブをクリックします。<br />3.値を変更、**アイコン**ボックス。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`.ico ファイルをアタッチします`Rf.ico`します。  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
