---
title: プログレスバー コントロールによって表示される値を設定する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: d295079a96ca19a4e4c98e113a3f3051c6403182
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141812"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>方法 : Windows フォーム ProgressBar コントロールによって表示される値を設定する
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripProgressBar> コントロールは、<xref:System.Windows.Forms.ProgressBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ProgressBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 .NET Framework では、<xref:System.Windows.Forms.ProgressBar>コントロール内の特定の値を表示する方法が複数用意されています。 どちらの方法を選択するかは、目の前のタスクや解決している問題によって異なります。 次の表に、選択できる方法を示します。  
  
|アプローチ|説明|  
|--------------|-----------------|  
|コントロールの値を<xref:System.Windows.Forms.ProgressBar>直接設定します。|この方法は、データ ソースからのレコードの読み取りなど、関連する項目の合計がわかっているタスクに役立ちます。 また、値を 1 回または 2 回だけ設定する必要がある場合は、簡単に設定できます。 最後に、プログレスバーに表示される値を減らす必要がある場合は、このプロセスを使用します。|  
|表示を<xref:System.Windows.Forms.ProgressBar>固定値で増やします。|この方法は、経過時間や既知の合計から処理されたファイル数など、最小と最大の間の単純なカウントを表示する場合に便利です。|  
|表示を<xref:System.Windows.Forms.ProgressBar>変化する値で増やします。|この方法は、表示される値を別の金額で何度も変更する必要がある場合に便利です。 たとえば、一連のファイルをディスクに書き込んでいるときに消費されるハード ディスク領域の量を示します。|  
  
 進行状況バーで表示される値を設定する最も直接的な方法は、プロパティ<xref:System.Windows.Forms.ProgressBar.Value%2A>を設定することです。 これは、デザイン時または実行時に行うことができます。  
  
### <a name="to-set-the-progressbar-value-directly"></a>進行状況バーの値を直接設定するには  
  
1. コントロールと<xref:System.Windows.Forms.ProgressBar><xref:System.Windows.Forms.ProgressBar.Minimum%2A><xref:System.Windows.Forms.ProgressBar.Maximum%2A>値を設定します。  
  
2. コードでは、コントロールの<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティを、設定した最小値と最大値の間の整数値に設定します。  
  
    > [!NOTE]
    > プロパティによって確立された<xref:System.Windows.Forms.ProgressBar.Value%2A>境界の外にプロパティを<xref:System.Windows.Forms.ProgressBar.Minimum%2A><xref:System.Windows.Forms.ProgressBar.Maximum%2A>設定すると、コントロールは例外を<xref:System.ArgumentException>スローします。  
  
     値を直接設定する方法を次のコード<xref:System.Windows.Forms.ProgressBar>例に示します。 このコードは、データ ソースからレコードを読み取り、データ レコードが読み取られるたびに進行状況バーとラベルを更新します。 この例では<xref:System.Windows.Forms.Label>、フォームにコントロール、<xref:System.Windows.Forms.ProgressBar>コントロール、および`CustomerRow``FirstName``LastName`フィールドとフィールドを呼び出す行を持つデータ テーブルが必要です。  
  
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
  
     一定の間隔で進行する進行状況を表示する場合は、値を設定し、その間隔でコントロールの値を増やす<xref:System.Windows.Forms.ProgressBar>メソッドを呼び出すことができます。 これは、進行状況を全体のパーセンテージとして測定していないタイマーやその他のシナリオに役立ちます。  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>進行状況バーを固定値で増やすには  
  
1. コントロールと<xref:System.Windows.Forms.ProgressBar><xref:System.Windows.Forms.ProgressBar.Minimum%2A><xref:System.Windows.Forms.ProgressBar.Maximum%2A>値を設定します。  
  
2. コントロールのプロパティを、<xref:System.Windows.Forms.ProgressBar.Step%2A>プログレス バーの表示値を増やす量を表す整数に設定します。  
  
3. プロパティに<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>設定された金額で表示される値を変更するには、メソッド<xref:System.Windows.Forms.ProgressBar.Step%2A>を呼び出します。  
  
     次のコード例は、進行状況バーがコピー操作でファイルの数を維持する方法を示しています。  
  
     次の例では、各ファイルがメモリに読み込まれると、進行状況バーとラベルが更新され、読み取られたファイルの合計が反映されます。 この例では、フォームにコントロールと<xref:System.Windows.Forms.Label>コントロールが含<xref:System.Windows.Forms.ProgressBar>まれている必要があります。  
  
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
  
     最後に、進行状況バーによって表示される値を増やして、各増加が一意の量になるようにすることができます。 これは、サイズの異なるファイルをハード ディスクに書き込んだり、進行状況を全体の割合として測定したりするなど、一連の一意の操作を追跡する場合に便利です。  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>進行状況バーを動的な値で増やすには  
  
1. コントロールと<xref:System.Windows.Forms.ProgressBar><xref:System.Windows.Forms.ProgressBar.Minimum%2A><xref:System.Windows.Forms.ProgressBar.Maximum%2A>値を設定します。  
  
2. 指定した<xref:System.Windows.Forms.ProgressBar.Increment%2A>整数で表示される値を変更するには、このメソッドを呼び出します。  
  
     次のコード例は、コピー操作中に使用されたディスク領域の量をプログレス バーで計算する方法を示しています。  
  
     次の例では、各ファイルがハード ディスクに書き込まれると、プログレス バーとラベルが更新され、ハード ディスクの空き容量が反映されます。 この例では、フォームにコントロールと<xref:System.Windows.Forms.Label>コントロールが含<xref:System.Windows.Forms.ProgressBar>まれている必要があります。  
  
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
