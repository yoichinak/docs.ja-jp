---
title: '方法: (LINQ) (Visual Basic) の区切り記号入りファイルのフィールドの順序を変更します。'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 25f860109275bdee1b980c68e71c2c65d44756a4
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593097"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>方法: (LINQ) (Visual Basic) の区切り記号入りファイルのフィールドの順序を変更します。
コンマ区切り (CSV) ファイルは、テキスト ファイルです。多くの場合、行と列で表されるスプレッドシート データや他の表形式データの格納に使用されます。 <xref:System.String.Split%2A> メソッドを使用してフィールドを区切ると、LINQ を使用した CSV ファイルのクエリと操作がとても簡単になります。 この手法は、CSV ファイルに限らず、行が構造化されているテキストの一部を並べ替えるときに利用できます。  
  
 次の例では、学生の "名"、"姓"、"ID" を表す 3 つの列があります。 これらのフィールドは、学生の姓に基づいてアルファベット順に並べられています。 クエリによって、ID 列が最初に表示され、学生の姓と名を結合して 2 列目に表示されるように列順を変えます。 行は ID フィールドの順に並べ替えられます。 結果は新しいファイルに保存され、元のデータは変更されません。  
  
### <a name="to-create-the-data-file"></a>データ ファイルを作成するには  
  
1. 次の行を、spreadsheet1.csv というプレーン テキスト ファイルにコピーします。 プロジェクト フォルダーにファイルを保存します。  
  
    ```  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a>例  
  
```vb  
Class CSVFiles  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data source.  
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")  
  
        ' Execute the query. Put field 2 first, then  
        ' reverse and combine fields 0 and 1 from the old field  
        Dim lineQuery = From line In lines   
                        Let x = line.Split(New Char() {","})   
                        Order By x(2)   
                        Select x(2) & ", " & (x(1) & " " & x(0))  
  
        ' Execute the query and write out the new file. Note that WriteAllLines  
        ' takes a string array, so ToArray is called on the query.  
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output to spreadsheet2.csv:  
' 111, Svetlana Omelchenko  
' 112, Claire O'Donnell  
' 113, Sven Mortensen  
' 114, Cesar Garcia  
' 115, Debra Garcia  
' 116, Fadi Fakhouri  
' 117, Hanying Feng  
' 118, Hugo Garcia  
' 119, Lance Tucker  
' 120, Terry Adams  
' 121, Eugene Zabokritski  
' 122, Michael Tucker  
```  
  
## <a name="see-also"></a>関連項目

- [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [LINQ とファイル ディレクトリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
- [方法: CSV ファイルから XML を生成する](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
