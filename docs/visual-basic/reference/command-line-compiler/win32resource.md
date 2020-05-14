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
ms.openlocfilehash: cee06adec89aac4b3e3f170df3bf932e466f3070
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004963"
---
# <a name="-win32resource"></a>-win32resource
Win32 リソース ファイルを出力ファイルに挿入します。  
  
## <a name="syntax"></a>構文  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 出力ファイルに追加するリソース ファイルの名前。 ファイル名に空白が含まれている場合は、名前を二重引用符 (" ") で囲みます。  
  
## <a name="remarks"></a>Remarks  
 Win32 リソース ファイルは、Microsoft Windows リソース コンパイラ (RC) を使用して作成することができます。  
  
 Win32 リソースは、バージョンまたはビットマップ (アイコン) 情報を格納することができ、**エクスプローラー**でアプリケーションを識別するのに役立ちます。 `-win32resource` を指定しない場合、コンパイラでアセンブリ バージョンに基づいてバージョン情報が生成されます。 `-win32resource` オプションと `-win32icon` オプションは同時に指定できません。  
  
 .NET Framework リソース ファイルの参照については「[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)」を、.NET Framework リソース ファイルのアタッチについては「[-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)」を参照してください。  
  
> [!NOTE]
> `-win32resource` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードでは `In.vb` がコンパイルされ、Win32 リソース ファイル `Rf.res` がアタッチされます。  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
