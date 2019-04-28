---
title: セキュリティと競合状態
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ceaedc7c38ae70a0db5a7fd584a765a7474aff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933810"
---
# <a name="security-and-race-conditions"></a>セキュリティと競合状態
問題の別の領域は、競合状態によって生じるセキュリティ ホールが発生する可能性です。 これが発生するいくつかの方法はあります。 次のサブトピックをアウトラインの主要な落とし穴を開発者は避ける必要があります。  
  
## <a name="race-conditions-in-the-dispose-method"></a>Dispose メソッドで競合状態  
 クラスの場合、 **Dispose**メソッド (詳細については、次を参照してください[ガベージ コレクション](../../../docs/standard/garbage-collection/index.md)) が同期されていないことができます内でクリーンアップ コード**Dispose**実行できる複数の。1 回、次の例に示すようにします。  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()   
{  
    if (myObj != null)   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 ため、この**Dispose**実装が同期されていない、可能性があります`Cleanup`最初の 1 つのスレッドとし前に、の 2 番目のスレッドによって呼び出される`_myObj`に設定されている**null**します。 これはセキュリティ上の問題であるかどうかによって起こる異なるときに、`Cleanup`コードの実行。 同期されていない主な課題**Dispose**実装は、ファイルなどのリソース ハンドルを使用します。 不適切な廃棄には、多くの場合、セキュリティの脆弱性につながる不適切なハンドルを使用することがあります。  
  
## <a name="race-conditions-in-constructors"></a>コンス トラクターでの競合状態  
 一部のアプリケーションでは、他のスレッドがそのクラス コンス トラクターが完全に実行する前にクラス メンバーにアクセスすることができる場合があります。 すべてのクラス コンス トラクターがないセキュリティの問題、発生するかに応じてスレッドを同期させる場合になっていることを確認するを確認してください。  
  
## <a name="race-conditions-with-cached-objects"></a>キャッシュされたオブジェクトの競合状態  
 セキュリティ情報をキャッシュしたり、コード アクセス セキュリティを使用するコード[Assert](../../../docs/framework/misc/using-the-assert-method.md)操作もされる恐れがあります競合状態、クラスの他の部分が適切に同期されていない場合、次の例に示すようにします。  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()   
{  
    if (SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()   
{  
    if (fCallersOK)   
    {  
        DoSomethingTrusted();  
    }  
    else   
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 他のパスがある場合`DoOtherWork`が同じオブジェクトと別のスレッドから呼び出すことできますが、信頼されていないの呼び出し元は、過去の需要を遅らせることができます。  
  
 コードは、セキュリティ情報をキャッシュする場合は、この脆弱性を確認することを確認します。  
  
## <a name="race-conditions-in-finalizers"></a>ファイナライザーでの競合状態  
 競合状態は、そのファイナライザーで解放し、静的またはアンマネージ リソースを参照するオブジェクトでも発生することができます。 複数のオブジェクトは、クラスのファイナライザーで操作されるリソースを共有している場合、オブジェクトは、そのリソースに対するすべてのアクセスを同期する必要があります。  
  
## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)
