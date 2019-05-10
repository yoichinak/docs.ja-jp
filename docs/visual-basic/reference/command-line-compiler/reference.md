---
title: -参照 (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: a205682bb15b5d25ba0a2df895533d3443a41409
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663465"
---
# <a name="-reference-visual-basic"></a>-参照 (Visual Basic)
コンパイラで型情報をコンパイルする現在のプロジェクトで使用できる、指定されたアセンブリでようにします。  
  
## <a name="syntax"></a>構文  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`fileList`|必須。 アセンブリ ファイル名のコンマ区切りリスト。 ファイル名に空白が含まれている場合は、名前を二重引用符で囲みます。|  
  
## <a name="remarks"></a>Remarks  
 ファイルをインポートするには、アセンブリ メタデータを含める必要があります。 パブリック型だけでは、アセンブリの外側に表示されます。 [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)オプションは、モジュールからメタデータをインポートします。  
  
 アセンブリ (アセンブリ A) を参照する場合は、別のアセンブリ (アセンブリ B) を参照する、場合、アセンブリ B を参照する必要があります。  
  
- アセンブリ A の型がアセンブリ B の型から継承されているか、アセンブリ B のインターフェイスを実装する。  
  
- アセンブリ B の戻り値の型またはパラメーターの型を使用するフィールド、プロパティ、イベント、またはメソッドが呼び出される。  
  
 使用[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)を 1 つ以上のアセンブリ参照があるディレクトリを指定します。  
  
 コンパイラがアセンブリ (モジュールではなく) 内の型を認識するには、型の解決を強制する必要があります。 これを実行する方法の 1 つの例では、型のインスタンスを定義します。 その他の方法、コンパイラのアセンブリ内の型名を解決するのには利用できます。 たとえば、アセンブリ内の型から継承する場合、型名し既知となるコンパイラに。  
  
 参照がよく使用される、Vbc.rsp 応答ファイル[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリでは、既定で使用されます。 使用して、`-noconfig`コンパイラが Vbc.rsp を使用したくない場合。  
  
 `-reference` の省略形は `/r` です。  
  
## <a name="example"></a>例  
 次のコマンドは、ソース ファイルをコンパイル`Input.vb`からの参照アセンブリと`Metad1.dll`と`Metad2.dll`を生成する`Out.exe`します。  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
