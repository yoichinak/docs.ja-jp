---
title: 型 '<typename1>' の値を '<typename2>' に変換できません。
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 027cccc9ad406d5bc2fd686ddeb4c674dc8f3c90
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621201"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>型の値 '\<typename1 >' に変換できません'\<typename2 >'。
型の値 '\<typename1 >' に変換できません。'\<typename2 >'。 型の不一致は、ファイル参照とアセンブリへの参照をプロジェクトの混合によって生じた可能性があります '\<assemblyname >'。 ファイル参照を置き換えてください '\<filepath >' プロジェクトで'\<projectname1 >' への参照をプロジェクトに '\<projectname2 >'。  
  
 プロジェクトがプロジェクト参照とファイル参照の両方を使用する場合、コンパイラは別に 1 つの型を変換できることを保証できません。  
  
 次の擬似コードは、このエラーを生成できる状況を示しています。  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 プロジェクト`P1`、間接的なプロジェクト参照をプロジェクトを通じて行います`P2`プロジェクトに`P3`へのファイルを直接参照も`P3`します。 宣言`commonObject`ファイル参照を使用して`P3`への呼び出し中に`P2.getCommonClass`へのプロジェクト参照を使用して`P3`します。  
  
 この状況で問題は、ファイル参照がファイルのパスと出力ファイルの名前を指定する`P3`(通常 p3.dll) プロジェクトの参照が、ソース プロジェクトを識別中に (`P3`) プロジェクトの名前。 このため、コンパイラは保証できませんが、型`P3.commonClass`2 つの異なる参照を使用して、同じソース コードに由来します。  
  
 通常このような状況が発生するプロジェクト参照とファイル参照が混在します。 上の図で、問題がない場合に発生する`P1`への参照を直接プロジェクトに加えられた`P3`ファイル参照の代わりにします。  
  
 **エラー ID:** BC30955  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- ファイル参照をプロジェクト参照を変更します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)
