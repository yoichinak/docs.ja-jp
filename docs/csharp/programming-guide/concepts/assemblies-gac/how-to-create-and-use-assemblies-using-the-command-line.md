---
title: '方法: コマンド ラインを使用してアセンブリを作成および使用する (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 12d23816b740816bd357c3c2ac57583f31bf3cb3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586029"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>方法: コマンド ラインを使用してアセンブリを作成および使用する (C#)
アセンブリとは、ダイナミック リンク ライブラリ (DLL) のことで、実行時にプログラムにリンクされます。 DLL のビルド例および使用例として、次に示すシナリオを考えてみます。  
  
- `MathLibrary.DLL`:実行時に呼び出されるメソッドが格納されているライブラリ ファイル。 この例では、DLL には 2 つのメソッド `Add` と `Multiply` が含まれています。  
  
- `Add`:`Add` メソッドが格納されているソース ファイル。 パラメーターの和を返します。 `Add` メソッドを含む `AddClass` クラスは `UtilityMethods` 名前空間のメンバーです。  
  
- `Mult`:`Multiply` メソッドが格納されているソース コード。 パラメーターの積を返します。 `Multiply` メソッドを含む `MultiplyClass` クラスも `UtilityMethods` 名前空間のメンバーです。  
  
- `TestCode`:`Main` メソッドが格納されているファイル。 DLL ファイルのメソッドを使用して、実行時引数の和と積を計算します。  
  
## <a name="example"></a>例  
  
```csharp  
// File: Add.cs   
namespace UtilityMethods  
{  
    public class AddClass   
    {  
        public static long Add(long i, long j)   
        {   
            return (i + j);  
        }  
    }  
}  
```  
  
```csharp  
// File: Mult.cs  
namespace UtilityMethods   
{  
    public class MultiplyClass  
    {  
        public static long Multiply(long x, long y)   
        {  
            return (x * y);   
        }  
    }  
}  
```  
  
```csharp  
// File: TestCode.cs  
  
using UtilityMethods;  
  
class TestCode  
{  
    static void Main(string[] args)   
    {  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:");  
  
        if (args.Length != 2)  
        {  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>");  
            return;  
        }  
  
        long num1 = long.Parse(args[0]);  
        long num2 = long.Parse(args[1]);  
  
        long sum = AddClass.Add(num1, num2);  
        long product = MultiplyClass.Multiply(num1, num2);  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum);  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product);  
    }  
}  
/* Output (assuming 1234 and 5678 are entered as command-line arguments):  
    Calling methods from MathLibrary.DLL:  
    1234 + 5678 = 6912  
    1234 * 5678 = 7006652          
*/  
```  
  
 このファイルには、DLL のメソッド `Add` と `Multiply` を使用するアルゴリズムが格納されています。 最初に、コマンド ラインから入力された引数 `num1` と `num2` を解析します。 次に、`AddClass` クラスの `Add` メソッドを使用して和を計算し、`MultiplyClass` クラスの `Multiply` メソッドを使って積を計算します。  
  
 ファイルの先頭で `using` ディレクティブを指定すると、次のように、コンパイル時に非修飾クラス名を使用して、DLL メソッドを参照できます。  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 ディレクティブを指定しない場合は、次のように、完全修飾名を使用する必要があります。  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>実行  
 プログラムを実行するには、次のように、EXE ファイルの名前と 2 つの数値を順に入力します。  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)
- [.NET のアセンブリ](../../../../standard/assembly/index.md)
- [DLL 関数を保持するクラスの作成](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
