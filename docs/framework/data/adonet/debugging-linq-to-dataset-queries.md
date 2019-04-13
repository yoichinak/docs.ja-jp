---
title: LINQ to DataSet クエリのデバッグ
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 0e015cc6042a21bf6d35915c3e19bfeb9b0dbb2a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133335"
---
# <a name="debugging-linq-to-dataset-queries"></a>LINQ to DataSet クエリのデバッグ

Visual Studio のデバッグをサポートしている[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]コード。 ただし、デバッグのいくつか違いがある[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]コードと非-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]マネージ コード。 ほとんどのデバッグ機能を使用[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]ステートメントをステップ実行、ブレークポイントの設定、デバッガー ウィンドウに表示される結果を表示するなど。 ただし、クエリの実行がデバッグ中に考慮すべきいくつかの副作用を遅延[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]コードし、はエディット コンティニュを使用するには、いくつか制限があります。 このトピックに固有のデバッグの側面を説明します。[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]と比較して非[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]マネージ コード。  
  
## <a name="viewing-results"></a>結果の表示  
 結果を表示することができます、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]データヒント、ウォッチ ウィンドウで、[クイック ウォッチ] ダイアログ ボックスを使用してステートメントです。 ソース ウィンドウで特定のクエリにポインターを置くと、データヒントが表示されます。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] の変数をコピーし、それを [ウォッチ] ウィンドウまたは [クイック ウォッチ] ダイアログ ボックスに貼り付けることができます。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、クエリが評価されるのは、実際にそのクエリが実行されたときです。作成または宣言した時点では評価されません。 これは呼び出されます*遅延実行*します。 したがって、それが評価されるまでは、クエリ変数に値は割り当てられません。 詳細については、次を参照してください。[で LINQ to DataSet クエリ](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)します。  
  
 デバッガーは、クエリの結果を表示するために、そのクエリを評価する必要があります。 この暗黙的な評価は、表示するときに発生します。、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]デバッガーでのクエリの結果がいくつかの効果を検討してください。 クエリの評価には時間がかかります。 結果ノードを展開するときにも時間を要します。 クエリによっては繰り返し評価が実行され、パフォーマンスが著しく低下する場合があります。 さらに、データの値またはプログラムの状態が変わるという副作用が伴う場合もあります。 すべてのクエリに副作用があるわけではありません。 副作用を伴うことなく安全にクエリを評価できるかどうかを判断するには、クエリが実装されているコードを十分に理解する必要があります。 詳細については、次を参照してください。[副作用と式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120))します。  
  
## <a name="edit-and-continue"></a>エディット コンティニュ  
 エディット コンティニュに変更をサポートしません[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。 追加、削除、または変更する場合、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]ステートメントではデバッグ セッション中に、ダイアログ ボックスが表示、変更がエディット コンティニュでサポートされていないを指示します。 このとき、変更を元に戻すか、デバッグ セッションを中止して編集済みのコードで新たなセッションを開始するかを選択できます。  
  
 さらに、編集し、続行が型やで使用されている変数の値の変更をサポートしていません、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]ステートメント。 この場合も、変更を元に戻すか、デバッグ セッションを中止して新たなセッションを開始するかを選択できます。  
  
 Visual C# で Visual Studio で、使うことはできませんエディット コンティニュを含むメソッドのコードに対して、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。  
  
 Visual Studio で Visual Basic で使えるエディット コンティニュで[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]を含むメソッドであっても、コード、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。 追加または前にコードを削除することができます、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]ステートメントでは、行番号が変わる場合でも、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。 デバッグのエクスペリエンス、Visual Basic 以外[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]前と同じコードまま[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]が導入されました。 変更、追加、または削除することはできません、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]変更を適用するデバッグを停止する場合を除き、ただし、クエリします。  
  
## <a name="see-also"></a>関連項目

- [マネージド コードのデバッグ](/visualstudio/debugger/debugging-managed-code)
- [プログラミング ガイド](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
