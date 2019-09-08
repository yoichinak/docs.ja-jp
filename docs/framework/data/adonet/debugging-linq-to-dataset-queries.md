---
title: LINQ to DataSet クエリのデバッグ
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: a82fd3e99a556daf40e5c65a16cf20278f38ea26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785214"
---
# <a name="debugging-linq-to-dataset-queries"></a>LINQ to DataSet クエリのデバッグ

Visual Studio では LINQ to DataSet コードのデバッグがサポートされています。 ただし、LINQ to DataSet コードと非 LINQ to DataSet マネージコードのデバッグにはいくつかの違いがあります。 ほとんどのデバッグ機能は、ステップ実行、ブレークポイントの設定、デバッガーウィンドウに表示される結果の表示など、LINQ to DataSet のステートメントで機能します。 ただし、でのクエリの遅延実行には、LINQ to DataSet コードのデバッグ中に考慮する必要がある副作用がいくつかあります。また、エディットコンティニュの使用にはいくつかの制限があります。 このトピックでは、LINQ to DataSet 以外のマネージコードと比較して LINQ to DataSet に固有のデバッグの側面について説明します。  
  
## <a name="viewing-results"></a>結果の表示  
 LINQ to DataSet ステートメントの結果を表示するには、DataTips、ウォッチウィンドウ、および [クイックウォッチ] ダイアログボックスを使用します。 ソース ウィンドウで特定のクエリにポインターを置くと、データヒントが表示されます。 LINQ to DataSet 変数をコピーして、ウォッチウィンドウまたは [クイックウォッチ] ダイアログボックスに貼り付けることができます。 LINQ to DataSet では、クエリは、クエリが実行されたときにのみ、作成または宣言されたときには評価されません。 これを*遅延実行*と呼びます。 したがって、それが評価されるまでは、クエリ変数に値は割り当てられません。 詳細については、「 [LINQ to DataSet のクエリ](queries-in-linq-to-dataset.md)」を参照してください。  
  
 デバッガーは、クエリの結果を表示するために、そのクエリを評価する必要があります。 この暗黙的な評価は、デバッガーで LINQ to DataSet クエリの結果を表示するときに発生し、考慮する必要があるいくつかの効果があります。 クエリの評価には時間がかかります。 結果ノードを展開するときにも時間を要します。 クエリによっては繰り返し評価が実行され、パフォーマンスが著しく低下する場合があります。 さらに、データの値またはプログラムの状態が変わるという副作用が伴う場合もあります。 すべてのクエリに副作用があるわけではありません。 副作用を伴うことなく安全にクエリを評価できるかどうかを判断するには、クエリが実装されているコードを十分に理解する必要があります。 詳細については、「[副作用と式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120))」を参照してください。  
  
## <a name="edit-and-continue"></a>エディット コンティニュ  
 エディットコンティニュは、LINQ to DataSet クエリへの変更をサポートしていません。 デバッグセッション中に LINQ to DataSet ステートメントを追加、削除、または変更した場合、エディットコンティニュでは変更がサポートされていないことを示すダイアログボックスが表示されます。 このとき、変更を元に戻すか、デバッグ セッションを中止して編集済みのコードで新たなセッションを開始するかを選択できます。  
  
 また、エディットコンティニュでは、LINQ to DataSet ステートメントで使用される変数の型または値の変更はサポートされていません。 この場合も、変更を元に戻すか、デバッグ セッションを中止して新たなセッションを開始するかを選択できます。  
  
 Visual Studio C#の visual Studio では、LINQ to DataSet クエリを含むメソッドのコードに対してエディットコンティニュを使用することはできません。  
  
 Visual Studio の Visual Basic では、LINQ to DataSet クエリを含むメソッドであっても、非 LINQ to DataSet コードでエディットコンティニュを使用できます。 変更が LINQ to DataSet クエリの行番号に影響する場合でも、LINQ to DataSet ステートメントの前にコードを追加または削除できます。 非 LINQ to DataSet コードの Visual Basic デバッグエクスペリエンスは、LINQ to DataSet が導入される前と同じままです。 ただし、変更を適用するためにデバッグを停止しない限り、LINQ to DataSet クエリを変更、追加、または削除することはできません。  
  
## <a name="see-also"></a>関連項目

- [マネージド コードをデバッグする](/visualstudio/debugger/debugging-managed-code)
- [プログラミング ガイド](programming-guide-linq-to-dataset.md)
