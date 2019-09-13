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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 256d9c9b825081e3bcfafd6e0e09de825d046d20
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894547"
---
# <a name="securing-exception-handling"></a>例外処理の保護
Visual C と Visual Basic では、スタックをさらにフィルター式の実行前に、**finally**ステートメント。 **キャッチ**に関連付けられているブロックの後にそのフィルターが実行される、**finally**ステートメント。 詳細については、「[ユーザーフィルター例外の使用](../../standard/exceptions/using-user-filtered-exception-handlers.md)」を参照してください。 このセクションでは、この順序のセキュリティへの影響について説明します。 フィルター ステートメントで順序を示す次の擬似コード例を検討してくださいと**finally**ステートメントを実行します。  
  
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
  
 このコードは、次を出力します。  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 フィルターを実行する前に、**finally**ステートメントでは、セキュリティの問題は状態を他のコードの実行が活用かかる場合がありますを変更することによってもたらされるようにします。 例:  
  
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
  
 この擬似コードを使用すると、スタックの上位にあるフィルターで任意のコードを実行できます。 その他の操作の例としては、別の id の一時的な偽装、セキュリティチェックをバイパスする内部フラグの設定、またはスレッドに関連付けられているカルチャの変更などがあります。 推奨される解決方法は、コードの変更を呼び出し元のフィルターブロックからスレッド状態に分離する例外ハンドラーを導入することです。 ただし、例外ハンドラーが正しく導入されていること、またはこの問題が解決されないことが重要です。 次の例では、UI カルチャを切り替えますが、あらゆる種類のスレッド状態変更が同様に公開される可能性があります。  
  
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
  
 修正プログラムがここでは、既存をラップする**try**/**finally**ブロックを**try**/**catch**ブロックです。 簡単に把握、 **catch、throw**既存句**try**/**finally**の次の例に示すように、ブロックで、問題が解決しません。  
  
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
  
 問題が解決しない、**finally**する前にステートメントが実行されていない、`FilterFunc`コントロールを取得します。  
  
 次の例は、ことを確認して問題を修正、**finally**句が呼び出し元の例外フィルター ブロックの例外を提供する前に実行します。  
  
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
