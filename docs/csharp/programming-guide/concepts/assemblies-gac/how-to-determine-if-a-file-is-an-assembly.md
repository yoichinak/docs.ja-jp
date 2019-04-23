---
title: '方法: ファイルがアセンブリであるかどうかを確認する (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: e8026ab5fa44b7601e54b5e76ebf9eb434596a07
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340140"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>方法: ファイルがアセンブリであるかどうかを確認する (C#)
ファイルが管理されていて、ファイルのメタデータにアセンブリ エントリが含まれている場合、そのファイルはアセンブリです。 アセンブリとメタデータの詳細については、「[アセンブリ マニフェスト](../../../../../docs/framework/app-domains/assembly-manifest.md)」を参照してください。  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>ファイルがアセンブリかどうかを手動で確認する方法  
  
1. [Ildasm.exe (IL 逆アセンブラー)](../../../../framework/tools/ildasm-exe-il-disassembler.md) を起動します。  
  
2. テストするファイルを読み込みます。  
  
3. **ILDASM** で、そのファイルが移植可能な実行可能 (PE) ファイルではないと報告された場合、そのファイルはアセンブリでありません。 詳細については、トピック「[方法: アセンブリの内容を表示する](../../../../framework/app-domains/how-to-view-assembly-contents.md)」を参照してください。  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>ファイルがアセンブリかどうかをプログラムによって確認する方法  
  
1. テストするファイルの完全パスと名前を渡して、<xref:System.Reflection.AssemblyName.GetAssemblyName%2A> メソッドを呼び出します。  
  
2. <xref:System.BadImageFormatException> 例外がスローされた場合、ファイルはアセンブリでありません。  
  
## <a name="example"></a>例  
 次の例では、DLL がアセンブリかどうかをテストして確認します。  
  
```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> メソッドはテスト ファイルを読み込み、情報が読み取られた時点で解放します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Reflection.AssemblyName>
- [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)
- [.NET のアセンブリ](../../../../standard/assembly/index.md)
