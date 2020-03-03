---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: 6ee842dbe65cbd9d147e77ec523a2b031d303738
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002390"
---
# <a name="-baseaddress"></a>-baseaddress
DLL を作成するときの既定のベースアドレスを指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>引数  
  
|項目|定義|  
|---|---|  
|`address`|必須。 DLL のベース アドレス。 このアドレスは16進数として指定する必要があります。|  
  
## <a name="remarks"></a>コメント  
 DLL の既定のベースアドレスは、.NET Framework によって設定されます。  
  
 このアドレスの下位ワードは丸められていることに注意してください。 たとえば、0x11110001 を指定すると、0x11110000 に丸められます。  
  
 DLL の署名プロセスを完了するには、厳密な名前付けツール (Sn.exe) の `–R` オプションを使用します。  
  
 ターゲットが DLL でない場合、このオプションは無視されます。  
  
|Visual Studio IDE で baseaddress を設定するには|  
|---|  
|1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2. **[コンパイル]** タブをクリックします。<br />3. **[詳細設定]** をクリックします。<br />4。 **[DLL のベースアドレス:]** ボックスの値を変更します。 **注:**     **Dll のベースアドレス:** box は、ターゲットが dll の場合を除き、読み取り専用です。|  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md))
