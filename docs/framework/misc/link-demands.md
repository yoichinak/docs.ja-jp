---
title: リンク確認要求
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ba3172b1a82c0a9f624a49eb63a193dd29faac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166992"
---
# <a name="link-demands"></a>リンク確認要求
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 リンク確認要求では、Just-In-Time コンパイル時にセキュリティ チェックが実行され、コードの直前の呼び出し元アセンブリだけがチェックされます。 リンクは、コードを関数ポインターの参照やメソッドの呼び出しなどの型の参照にバインドするときに発生します。 呼び出し元のアセンブリが、コードにリンクするための十分な権限を持たない場合は、リンクは許可されず、コードが読み込まれて実行されると、ランタイム例外がスローされます。 リンク確認要求は、コードから継承するクラスでオーバーライドできます。  
  
 この種類の要求では、完全なスタック ウォークが実行されないことと、コードがおびき寄せによる攻撃を受ける可能性があることに注意してください。 たとえば、アセンブリ A 内のメソッドは、リンク確認要求によって保護されているが場合、アセンブリ B の直接の呼び出し元はに基づいて評価アセンブリ B のアクセス許可 ただし、リンク確認要求を評価しませんアセンブリ C のメソッドを間接的に呼び出すメソッドでアセンブリ B. メソッドを使用して、アセンブリの場合リンク確認要求では、直前の呼び出し元のアセンブリ内の呼び出し元は、コードへのリンクになっている可能性がありますが直接アクセス許可のみを指定します。 すべての呼び出し元がコードを実行するために必要なアクセス許可は指定しません。  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>、<xref:System.Security.CodeAccessPermission.Deny%2A>、および <xref:System.Security.CodeAccessPermission.PermitOnly%2A> の各スタック ウォーク修飾子は、リンク確認要求の評価に影響を与えません。  リンク確認要求は、スタック ウォークを実行しないため、スタック ウォーク修飾子はリンク確認要求に影響を与えません。  
  
 かどうかによってはリンク確認要求によって保護されているメソッドにアクセスが[リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)、リンク確認要求は、リフレクションによってアクセスされたコードの直前の呼び出し元を確認します。 これは、メソッドの探索と、リフレクションを使用して行うメソッド呼び出しの両方に該当します。 たとえば、コードでは、リフレクションを使用して、返します、<xref:System.Reflection.MethodInfo>オブジェクトのメソッドを表すリンク確認要求によって保護されているし、して渡されます**MethodInfo**の他のコードを元のメソッドを呼び出すオブジェクトを使用するオブジェクト。 ここで、リンク確認要求のチェックは 2 回に発生します。 を返すコードに対して 1 回、 **MethodInfo**オブジェクトとそれを呼び出すコードに 1 回です。  
  
> [!NOTE]
>  静的クラスのコンストラクターで実行されるリンク確認要求では、静的コンストラクターは保護されません。これは、静的コンストラクターがアプリケーションのコードの実行パスの外側で、システムによって呼び出されるためです。 その結果、リンク確認要求がクラス全体に適用される場合、静的コンストラクターへのアクセスは保護できませんが、クラスの残りの部分は保護されます。  
  
 次のコード フラグメントでは、`ReadData` メソッドにリンクするコードはすべて `CustomPermission` のアクセス許可を持つ必要があることを宣言によって指定しています。 このアクセス許可は架空のカスタム許可であり、.NET Framework には実在しません。 渡すことによって、要求が行われた、 **SecurityAction.LinkDemand**フラグを`CustomPermissionAttribute`します。  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function    
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a>関連項目

- [属性](../../../docs/standard/attributes/index.md)
- [コード アクセス セキュリティ](../../../docs/framework/misc/code-access-security.md)
