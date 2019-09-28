---
title: '方法: Visual Basic から COM オブジェクトを参照する'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 8e502dc9a279d9271a61fd2cf7a6afb564f09125
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351999"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>方法: Visual Basic から COM オブジェクトを参照する
Visual Basic では、タイプライブラリを持つ COM オブジェクトへの参照を追加するには、COM ライブラリ用の相互運用機能アセンブリを作成する必要があります。 COM オブジェクトのメンバーへの参照は相互運用機能アセンブリにルーティングされ、実際の COM オブジェクトに転送されます。 COM オブジェクトからの応答は相互運用機能アセンブリにルーティングされ、.NET Framework アプリケーションに転送されます。  
  
 .NET アセンブリに COM オブジェクトの型情報を埋め込むことによって、相互運用機能アセンブリを使用せずに COM オブジェクトを参照できます。 型情報を埋め込むには、COM オブジェクトへの参照の `Embed Interop Types` プロパティを `True` に設定します。 コマンドラインコンパイラを使用してコンパイルする場合は、`/link` オプションを使用して COM ライブラリを参照します。 詳細については、「 [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)」を参照してください。  
  
 統合開発環境 (IDE: integrated development environment) からタイプライブラリへの参照を追加すると、Visual Basic によって相互運用機能アセンブリが自動的に作成されます。 コマンドラインから作業する場合は、Tlbimp ユーティリティを使用して、相互運用機能アセンブリを手動で作成できます。  
  
### <a name="to-add-references-to-com-objects"></a>COM オブジェクトへの参照を追加するには  
  
1. **[プロジェクト]** メニューの **[参照の追加]** をクリックし、ダイアログボックスの **[COM]** タブをクリックします。  
  
2. COM オブジェクトの一覧から、使用するコンポーネントを選択します。  
  
3. 相互運用機能アセンブリへのアクセスを簡単にするには、COM オブジェクトを使用するクラスまたはモジュールの先頭に @no__t 0 ステートメントを追加します。 たとえば、次のコード例では、`Microsoft InkEdit Control 1.0` ライブラリで参照されているオブジェクトの名前空間 `INKEDLib` をインポートします。  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Tlbimp を使用して相互運用機能アセンブリを作成するには  
  
1. まだ検索パスに含まれておらず、現在のディレクトリに存在しない場合は、Tlbimp の場所を検索パスに追加します。  
  
2. コマンドプロンプトから Tlbimp を呼び出し、次の情報を指定します。  
  
    - タイプライブラリを含む DLL の名前と場所  
  
    - 情報を配置する名前空間の名前と場所  
  
    - ターゲット相互運用機能アセンブリの名前と場所  
  
     次にコード例を示します。  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Tlbimp.exe を使用して、登録されていない COM オブジェクトに対しても、タイプライブラリの相互運用機能アセンブリを作成できます。 ただし、相互運用機能アセンブリによって参照される COM オブジェクトは、それらが使用されるコンピューターに適切に登録されている必要があります。 Windows オペレーティングシステムに含まれている Regsvr32 ユーティリティを使用して、COM オブジェクトを登録できます。  
  
## <a name="see-also"></a>関連項目

- [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [チュートリアル: COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
