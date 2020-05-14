---
title: 型 '<typename1>' の値を '<typename2>' に変換することはできません。(複数ファイル参照)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 7371cbd4fef4abced95744071ff222b40e160e3e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620307"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>型 '\<typename1>' の値を '\<typename2>' に変換することはできません (複数ファイル参照)
型 '\<typename1>' の値を '\<typename2>' に変換できません。 型の不一致の原因として、プロジェクト '\<projectname1>' の '\<filepath1>' へのファイル参照と、プロジェクト '\<projectname2>' の '\<filepath2>' へのファイル参照が混在していることが考えられます。 両方のアセンブリが同一である場合は、これらの参照を同じ場所から参照するように置き換えてください。  
  
 プロジェクトが 1 つのアセンブリに対して複数のファイル参照を作成する場合、コンパイラは、1 つの型を別の型に変換できることを保証できません。  
  
 各ファイル参照は、プロジェクトの出力ファイルのファイル パスと名前を指定します (通常は DLL ファイル)。 コンパイラは、出力ファイルが同じソースからのものであること、または同じアセンブリの同じバージョンを表していることを保証できません。 そのため、異なる参照内の型が同じ型であるか、またはある型を他の型に変換できるかを保証できません。  
  
 参照されるアセンブリのアセンブリ ID が同じであることがわかっている場合は、1 つのファイル参照を使用できます。 *アセンブリ ID* には、アセンブリの名前、バージョン、公開キー (存在する場合)、およびカルチャが含まれます。 この情報はアセンブリを一意に識別します。  
  
 **エラー ID:** BC30961  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 参照アセンブリのアセンブリ ID が同じである場合は、ファイル参照の 1 つを削除するか置き換えて、ファイル参照が 1 つだけになるようにします。  
  
- 参照アセンブリのアセンブリ ID が同じでない場合は、コードを変更して、一方の型のもう一方の型への変換を試みないようにします。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)
