---
title: バイナリ データの取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 9acda6631e17031a81ba06d9530739a586fac7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794432"
---
# <a name="retrieving-binary-data"></a>バイナリ データの取得
既定では、 **DataReader**は、データ行全体が使用可能になるとすぐに、受信データを行として読み込みます。 バイナリ ラージ オブジェクト (BLOB) には、1 行に収まらない数ギガバイトのデータが含まれる場合があるため、別の処理が必要です。 **ExecuteReader**メソッドには、 **DataReader**の既定の動作を変更<xref:System.Data.CommandBehavior>するための引数を受け取るオーバーロードがあります。 ExecuteReader メソッドに<xref:System.Data.CommandBehavior.SequentialAccess>を渡して**DataReader**の既定の動作を変更することで、データの行を読み込む代わりに、データを受信したときにシーケンシャルにデータが読み込まれるようにすることができます。 これは BLOB やその他の大きなデータ構造を読み込む場合に理想的な処理です。 この動作は、データ ソースによって異なる場合があります。 たとえば、Microsoft Access から BLOB を返すと、受け取ったデータから順に読み込むのではなく、BLOB 全体をメモリに読み込みます。  
  
 **SequentialAccess**を使用するように**DataReader**を設定するときは、返されるフィールドにアクセスする順序に注意する必要があります。 **DataReader**の既定の動作では、行全体が使用可能になるとすぐに読み込まれるので、次の行が読み込まれるまで、任意の順序で返されたフィールドにアクセスできます。 ただし、 **SequentialAccess**を使用する場合は、 **DataReader**によって返されるフィールドに順番にアクセスする必要があります。 たとえば、クエリが 3 つの列 (3 番目の列は BLOB) を返す場合、最初のフィールドおよび 2 番目のフィールドの値は、3 番目のフィールドの BLOB データにアクセスする前に返す必要があります。 最初のフィールドまたは 2 番目のフィールドの前に 3 番目のフィールドにアクセスした場合は、最初のフィールドと 2 番目のフィールドの値は使用できなくなります。 これは、 **SequentialAccess**がデータを順番に返すように**datareader**を変更し、 **datareader**がそれを読み取った後にデータを使用できないためです。  
  
 BLOB フィールドのデータにアクセスするときは、 **DataReader**の**GetBytes**または**GetChars**型指定されたアクセサーを使用して、配列にデータを格納します。 文字データには**GetString**を使用することもできます。ただし. システム リソースを節約するためには、BLOB 値全体を 1 つの文字列変数に読み込むことは望ましくありません。 特定のバッファー サイズのデータを返すように指定する代わりに、返されたデータから読み込む先頭バイトまたは先頭文字の開始位置を指定できます。 **GetBytes**と**GetChars** `long`は、返されるバイト数または文字数を表す値を返します。 Null 配列を**GetBytes**または**GetChars**に渡すと、返される long 値は BLOB の合計バイト数または文字数になります。 オプションで、データ読み込みの開始位置を示す、配列内のインデックスを指定できます。  
  
## <a name="example"></a>例  
 次の例では、Microsoft SQL Server の**pubs**サンプルデータベースから発行者 ID とロゴが返されます。 発行者 ID (`pub_id`) は文字フィールドであり、ロゴはイメージ、つまり、BLOB です。 **Logo**フィールドはビットマップであるため、この例では、 **GetBytes**を使用してバイナリデータを返します。 フィールドには順番にアクセスする必要があるため、現在の行のデータに対して発行者 ID はロゴの前にアクセスされることに注意してください。  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream                   
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter                 
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100        
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte    
' The bytes returned from GetBytes.  
Dim retval As Long                     
' The starting position in the BLOB output.  
Dim startIndex As Long = 0             
  
' The publisher id to use in the file name.  
Dim pubID As String = ""              
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;                            
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;                          
  
// Size of the BLOB buffer.  
int bufferSize = 100;                     
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];    
// The bytes returned from GetBytes.  
long retval;                              
// The starting position in the BLOB output.  
long startIndex = 0;                      
  
// The publisher id to use in the file name.  
string pubID = "";                       
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);    
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a>関連項目

- [SQL Server のバイナリ データと大きな値のデータ](./sql/sql-server-binary-and-large-value-data.md)
- [ADO.NET の概要](ado-net-overview.md)
