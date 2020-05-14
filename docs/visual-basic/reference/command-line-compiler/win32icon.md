---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 6b4b69d227c857442de6857fac023090b3698e81
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004632"
---
# <a name="-win32icon"></a>-win32icon
.ico ファイルを出力ファイルに挿入します。 この .ico ファイルは、**エクスプローラー**では出力ファイルを表します。  
  
## <a name="syntax"></a>構文  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`filename`|出力ファイルに追加する .ico ファイル。 ファイル名に空白が含まれている場合は、名前を二重引用符 (" ") で囲みます。|  
  
## <a name="remarks"></a>Remarks  
 Microsoft Windows リソース コンパイラ (RC) を使用して .ico ファイルを作成することができます。 リソース コンパイラは、Visual C++ プログラムをコンパイルするときに呼び出されます。 .ico ファイルは .rc ファイルから作成されます。 `-win32icon` オプションと `-win32resource` オプションは同時に指定できません。  
  
 .NET Framework リソース ファイルの参照については「[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)」を、.NET Framework リソース ファイルのアタッチについては「[-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)」を参照してください。 .res ファイルのインポートについては、「[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)」を参照してください。  
  
|Visual Studio IDE で -win32icon を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2. **[アプリケーション]** タブをクリックします。<br />3. **[アイコン]** ボックスの値を変更します。|  
  
## <a name="example"></a>例  
 次のコードでは `In.vb` がコンパイルされ、.ico ファイル `Rf.ico` がアタッチされます。  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
