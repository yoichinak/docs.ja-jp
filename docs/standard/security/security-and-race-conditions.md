---
title: セキュリティと競合状態
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
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
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186780"
---
# <a name="security-and-race-conditions"></a>セキュリティと競合状態
もう一つの懸念事項は、レース条件によって悪用されるセキュリティホールの可能性です。 これが起こるいくつかの方法があります。 次のサブトピックでは、開発者が避けなければならないいくつかの主な落とし穴の概要を説明します。  
  
## <a name="race-conditions-in-the-dispose-method"></a>Dispose メソッドの競合条件  
 クラスの**Dispose**メソッド (詳細については、「[ガベージ コレクション](../../../docs/standard/garbage-collection/index.md)」を参照) が同期されていない場合、次の例に示すように **、Dispose**内のクリーンアップ コードを複数回実行できます。  
  
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
  
 この**Dispose**実装は同期されていないため、最初の`Cleanup`1 つのスレッドから呼び出し、次に 2`_myObj`つ目のスレッドを呼び出す場合は**null**に設定できます。 これがセキュリティ上の問題であるかどうかは、コードの`Cleanup`実行時に何が起こるかによって異なります。 非同期**の Dispose**実装に関する大きな問題は、ファイルなどのリソース ハンドルの使用です。 不適切な破棄により、不適切なハンドルが使用され、セキュリティの脆弱性が発生する場合があります。  
  
## <a name="race-conditions-in-constructors"></a>コンストラクタの競合状況  
 アプリケーションによっては、クラス コンストラクターが完全に実行される前に、他のスレッドがクラス メンバーにアクセスできる場合があります。 すべてのクラス コンストラクターを確認して、セキュリティ上の問題が発生しないかどうかを確認するか、必要に応じてスレッドを同期する必要があります。  
  
## <a name="race-conditions-with-cached-objects"></a>キャッシュされたオブジェクトを含む競合条件  
 セキュリティ情報をキャッシュするコード、またはコード アクセス セキュリティ[Assert](../../../docs/framework/misc/using-the-assert-method.md)操作を使用するコードは、次の例に示すように、クラスの他の部分が適切に同期されていない場合にも競合状態に対して脆弱になる可能性があります。  
  
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
  
 同じオブジェクトを`DoOtherWork`持つ別のスレッドから他のパスを呼び出すことができる場合、信頼されていない呼び出し元は要求を超えてスリップできます。  
  
 コードでセキュリティ情報がキャッシュされる場合は、この脆弱性について確認してください。  
  
## <a name="race-conditions-in-finalizers"></a>ファイナライザーのレース条件  
 競合状態は、静的リソースまたはアンマネージ リソースを参照するオブジェクトで発生し、ファイナライザーで解放されることもあります。 クラスのファイナライザーで操作されるリソースを複数のオブジェクトが共有する場合、そのオブジェクトは、そのリソースへのすべてのアクセスを同期する必要があります。  
  
## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)
