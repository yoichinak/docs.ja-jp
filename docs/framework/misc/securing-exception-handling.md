---
title: 例外処理の保護
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
ms.openlocfilehash: ad27e62197f6fdaa6b5e706f4ae02c03fecae9f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181137"
---
# <a name="securing-exception-handling"></a>例外処理の保護
Visual C++ および Visual Basic では、フィルター式が、最終的**なステートメント**の前に、スタックの上方に実行されます。 そのフィルターに関連付けられた**catch**ブロックは **、finally**ステートメントの後に実行されます。 詳細については、「[ユーザーフィルター処理例外の使用](../../standard/exceptions/using-user-filtered-exception-handlers.md)」を参照してください。 このセクションでは、この順序のセキュリティへの影響について説明します。 フィルター ステートメントと**finally**ステートメントの実行順序を示す次の擬似コード例を考えてみます。  
  
```cpp  
void Main()
{  
    try
    {  
        Sub();  
    }
    except (Filter())
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()
{  
    try
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }
    finally
    {  
        Console.WriteLine("finally");  
    }  
}
```  
  
 このコードは、次のコードを出力します。  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 フィルターは**finally**ステートメントの前に実行されるため、他のコードの実行が利用できる状態の変更を行う何かによってセキュリティの問題を導入できます。 次に例を示します。  
  
```cpp  
try
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and
    // so on) that could be exploited if malicious
    // code ran before state is restored.  
    Do_some_work();  
}
finally
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 この擬似コードを使用すると、スタックの上位にあるフィルタで任意のコードを実行できます。 同様の効果を持つ操作の他の例としては、別の ID の一時的な偽装、セキュリティ チェックをバイパスする内部フラグの設定、またはスレッドに関連付けられたカルチャの変更があります。 推奨される解決策は、例外ハンドラーを導入して、コードのスレッド状態への変更を呼び出し元のフィルター ブロックから分離することです。 ただし、例外ハンドラが適切に導入されているか、この問題が解決されないことが重要です。 次の例では、UI カルチャを切り替えますが、スレッド状態の変更の種類は同様に公開できます。  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 この場合の修正は、既存の**try**/**finally**ブロックを**try**/**catch**ブロックにラップする方法です。 次の例に示すように **、catch-throw**句を既存の**try**/**finally**ブロックに導入するだけでは問題は解決しません。  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 finally**ステートメントが**制御を取得する前に実行されていないため、この方法`FilterFunc`では問題は解決しません。  
  
 次の例では、呼び出し元の例外フィルター ブロックを例外を提供する前に**finally**句が実行されたことを確認することで、問題を解決します。  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try
    {  
        try
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](../../standard/security/secure-coding-guidelines.md)
