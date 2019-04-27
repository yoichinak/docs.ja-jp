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
ms.openlocfilehash: bc8cd20a4183ffd002f1399b6b50c8956208a21b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868804"
---
# <a name="securing-exception-handling"></a>例外処理の保護
Visual C と Visual Basic では、スタックをさらにフィルター式の実行前に、**最後に**ステートメント。 **キャッチ**に関連付けられているブロックの後にそのフィルターが実行される、**最後に**ステートメント。 詳細については、次を参照してください。[ユーザー フィルター例外](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)します。 このセクションでは、この注文のセキュリティへの影響を調べます。 フィルター ステートメントで順序を示す次の擬似コード例を検討してくださいと**最後に**ステートメントを実行します。  
  
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
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 フィルターを実行する前に、**最後に**ステートメントでは、セキュリティの問題は状態を他のコードの実行が活用かかる場合がありますを変更することによってもたらされるようにします。 例:  
  
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
  
 この擬似コードは、任意のコードを実行するスタックの上位フィルターを使用できます。 他の同様の効果を必要とされる操作の例がいくつかのセキュリティ チェックをバイパスする内部フラグを設定、別の id の一時的な権限の借用またはスレッドに関連付けられているカルチャを変更します。 スレッドの状態に呼び出し元のフィルターのブロックから、コードの変更を分離する例外ハンドラーを導入することをお勧めします。 ただし、例外ハンドラーを正しく導入することが重要か、この問題は解消されません。 次の例では、スイッチ、UI カルチャが、任意の種類のスレッド状態の変更を同様に公開される可能性があります。  
  
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
  
 修正プログラムがここでは、既存をラップする**お試しください**/**最後に**ブロックを**お試しください**/**キャッチ**ブロックです。 簡単に把握、 **catch、throw**既存句**お試しください**/**最後に**の次の例に示すように、ブロックで、問題が解決しません。  
  
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
  
 問題が解決しない、**最後に**する前にステートメントが実行されていない、`FilterFunc`コントロールを取得します。  
  
 次の例は、ことを確認して問題を修正、**最後に**句が呼び出し元の例外フィルター ブロックの例外を提供する前に実行します。  
  
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

- [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)
