---
title: プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 7c05c712bcbb0a61bb3121bb71a7823a1c29afb5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625583"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました
プロジェクトでは、XML スキーマのコンパイル中にエラーが発生しました。 このため、XML IntelliSense は使用できません。  
  
 プロジェクトに含まれる XML スキーマ定義 (XSD) スキーマでエラーがあります。 このエラーは、既存の XSD スキーマとの競合がプロジェクトに設定する XSD スキーマ (.xsd) ファイルを追加するときに発生します。  
  
 **エラー ID:** BC36810  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 警告をダブルクリック、**エラー リスト**ウィンドウ。 Visual Basic では、警告のソースである XSD ファイルの場所を実行します。 XSD スキーマでエラーを修正します。  
  
- 必要なすべての XSD スキーマ (.xsd) ファイルがプロジェクトに含まれることを確認します。 をクリックする必要があります**すべてのファイル**上、**プロジェクト**メニュー、.xsd ファイル**ソリューション エクスプ ローラー**。 .Xsd ファイルを右クリックし、をクリックし、**プロジェクトに含める**ファイルをプロジェクトに含める。  
  
- XML to Schema ウィザードを使用している場合、同じソースから 1 回以上のスキーマを推論する場合にこのエラーが発生することができます。 スキーマ項目のテンプレートに新しい XML がこの場合、既存の XSD スキーマ ファイルを削除するには、プロジェクトから追加し、提供して XML to Schema ウィザード適用可能なすべての XML ソース プロジェクトの。  
  
- XSD スキーマのエラーが識別されない場合、XML コンパイラに詳細なエラー メッセージを提供するための十分な情報ことはできません。 場合に、プロジェクトの一致に含まれる .xsd ファイルの XML 名前空間が、Visual Studio で設定する XML スキーマで特定された XML 名前空間を使用することを確認するより詳細なエラー情報を取得することができます。  
  
## <a name="see-also"></a>関連項目

- [[エラー一覧] ウィンドウ](/visualstudio/ide/reference/error-list-window)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
