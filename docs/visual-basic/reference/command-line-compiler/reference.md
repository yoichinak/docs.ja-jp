---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 35e02d1ad4409e754c2466f7d0ae7e68214772e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716706"
---
# <a name="-reference-visual-basic"></a>-reference (Visual Basic)
コンパイラによって、指定されたアセンブリ内の型情報を、現在のコンパイル対象のプロジェクトで使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
-reference:fileList  
```

or

```console
-r:fileList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`fileList`|必須です。 アセンブリ ファイル名のコンマ区切りリスト。 ファイル名に空白が含まれている場合は、名前を二重引用符で囲みます。|  
  
## <a name="remarks"></a>Remarks  
 インポートするファイルには、アセンブリ メタデータが含まれている必要があります。 アセンブリ外で表示されるのはパブリック型のみです。 [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) オプションでは、モジュールからメタデータをインポートします。  
  
 あるアセンブリ (アセンブリ A) を参照していて、それ自体では別のアセンブリ (アセンブリ B) が参照される場合、次の場合はアセンブリ B を参照する必要があります。  
  
- アセンブリ A の型がアセンブリ B の型から継承されているか、アセンブリ B のインターフェイスを実装する。  
  
- アセンブリ B の戻り値の型またはパラメーターの型を使用するフィールド、プロパティ、イベント、またはメソッドが呼び出される。  
  
 1 つまたは複数のアセンブリ参照が配置されているディレクトリを指定するには、[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) を使用します。  
  
 コンパイラで (モジュールではなく) アセンブリの型を認識するには、型を強制的に解決する必要があります。 これを行う方法の 1 つの例は、型のインスタンスを定義することです。 コンパイラのアセンブリの型名を解決するために、他の方法を使用できます。 たとえば、アセンブリの型から継承する場合、型名はコンパイラに認識されるようになります。  
  
 既定では、よく使われる .NET Framework アセンブリを参照する Vbc.rsp 応答ファイルが使用されます。 コンパイラで Vbc.rsp が使われないようにする場合は、`-noconfig` を使用します。  
  
 `-reference` の省略形は `-r` です。  
  
## <a name="example"></a>例  
 次のコマンドでは、ソース ファイル `Input.vb` と、`Metad1.dll` および `Metad2.dll` からの参照アセンブリをコンパイルして、`Out.exe` を生成します。  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
