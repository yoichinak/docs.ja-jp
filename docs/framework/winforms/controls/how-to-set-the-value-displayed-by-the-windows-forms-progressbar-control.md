---
title: '方法: Windows フォーム ProgressBar コントロールによって表示される値を設定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: a889d6e5cd40833353c1b294031621b7b289ac4d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715894"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>方法: Windows フォーム ProgressBar コントロールによって表示される値を設定します。
> [!IMPORTANT]
>  
  <xref:System.Windows.Forms.ToolStripProgressBar> コントロールは、<xref:System.Windows.Forms.ProgressBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ProgressBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]内で指定された値を表示するいくつかの方法を提供する、<xref:System.Windows.Forms.ProgressBar>コントロール。 どのアプローチを選択するは、手元のタスクまたは当面の問題によって異なります。 選択することができます、方法を次の表に示します。  
  
|方法|説明|  
|--------------|-----------------|  
|値を設定、<xref:System.Windows.Forms.ProgressBar>直接制御します。|この方法は、データ ソースからレコードの読み取りなど、関連する測定する項目の合計がわかっている場合のタスクに役立ちます。 さらに、値を 1 ~ 2 回設定する必要がある場合、簡単にこれを行う方法になります。 最後に、進行状況バーに表示される値を小さく必要がある場合は、このプロセスを使用します。|  
|増やす、<xref:System.Windows.Forms.ProgressBar>固定値を表示します。|この方法は、最小値と最大値、または既知の全体の中から処理されたファイルの数の経過時間などの単純なカウントを表示しているときに便利です。|  
|増やす、<xref:System.Windows.Forms.ProgressBar>が変化する値を表示します。|このアプローチは、表示されている値をそれぞれ異なる量の回数を変更する必要がある場合に便利です。 たとえば、一連のファイルをディスクに書き込み中に使用しているハード_ディスク領域の量を表示する場合します。|  
  
 進行状況バーに表示される値を設定する最も直接的な方法は、設定して、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティ。 これは、デザイン時または実行時に行うことができます。  
  
### <a name="to-set-the-progressbar-value-directly"></a>プログレス バーの値を直接設定するには  
  
1.  設定、<xref:System.Windows.Forms.ProgressBar>コントロールの<xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>値。  
  
2.  コードでは、設定、コントロールの<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティを設定した最小値と最大値までの整数値。  
  
    > [!NOTE]
    >  設定した場合、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティを確立する境界の外側、<xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>プロパティ、コントロールがスローされます、<xref:System.ArgumentException>例外。  
  
     次のコード例を設定する方法を示しています、<xref:System.Windows.Forms.ProgressBar>直接値します。 コードでは、データ ソースからレコードを読み取りし、データ レコードが読み取られるたびに、進行状況バーとラベルを更新します。 この例は、フォームに、<xref:System.Windows.Forms.Label>コントロール、<xref:System.Windows.Forms.ProgressBar>制御、およびと呼ばれる行のデータ テーブル`CustomerRow`で`FirstName`と`LastName`フィールド。  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     固定間隔での進行状況を表示する場合は、値の設定し、を増加させるメソッドを呼び出して、<xref:System.Windows.Forms.ProgressBar>その間隔でのコントロールの値。 これは、タイマーおよびを測定していない進行状況全体に占める割合として他のシナリオに便利です。  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>進行状況バーを固定値を増やします  
  
1.  設定、<xref:System.Windows.Forms.ProgressBar>コントロールの<xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>値。  
  
2.  コントロールの設定<xref:System.Windows.Forms.ProgressBar.Step%2A>に進行状況バーの量を表す整数のプロパティに値が表示されます。  
  
3.  呼び出す、<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>に設定した値に表示される値を変更するメソッドを<xref:System.Windows.Forms.ProgressBar.Step%2A>プロパティ。  
  
     次のコード例では、進行状況バーが、コピー操作でファイルの数を維持する方法を示しています。  
  
     次の例では、各ファイルは、メモリに読み込み、進行状況バーとラベルは反映する更新ファイルの合計数を読み取る。 この例は、フォームに、<xref:System.Windows.Forms.Label>コントロールと<xref:System.Windows.Forms.ProgressBar>コントロール。  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     最後に、それぞれの増加が異なる量ように進行状況バーに表示される値を増やすことができます。 これは、機能は、一連のハード _ ディスクの場合は、さまざまなサイズのファイルの書き込みや、全体に占める割合として進行状況を測定するなどの一意の操作の追跡を維持することがときに便利です。  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>動的な値で進行状況バーを向上させる  
  
1.  設定、<xref:System.Windows.Forms.ProgressBar>コントロールの<xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>値。  
  
2.  呼び出す、<xref:System.Windows.Forms.ProgressBar.Increment%2A>メソッドを指定する整数値に表示される値を変更します。  
  
     次のコード例では、どのように、コピー操作中にディスク領域が使用されている進行状況バーが計算を示しています。  
  
     次の例では、各ファイルが、ハード ディスクに書き込まれると、進行状況バーとラベル更新されます使用可能なハード_ディスク領域の量を反映するように。 この例は、フォームに、<xref:System.Windows.Forms.Label>コントロールと<xref:System.Windows.Forms.ProgressBar>コントロール。  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number   
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number   
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example   
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of   
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_   
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number   
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and   
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number   
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example   
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of   
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [ProgressBar コントロールの概要](progressbar-control-overview-windows-forms.md)
- [ProgressBar コントロール](progressbar-control-windows-forms.md)
