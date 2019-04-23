---
title: プリンシパル オブジェクトの置き換え
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f33be207dd6166b16a04844f3d92b6e017d1c7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345444"
---
# <a name="replacing-a-principal-object"></a>プリンシパル オブジェクトの置き換え
認証サービスを提供するアプリケーションでは、特定のスレッドの **プリンシパル** オブジェクト (<xref:System.Security.Principal.IPrincipal>) を置換する必要があります。 さらに、虚偽の ID やロールを要求することにより、悪意をもってアタッチされた不適切な **プリンシパル** がアプリケーションのセキュリティに問題を生じさせるため、セキュリティ システムを活用して **プリンシパル** オブジェクトを置き換える機能を保護する必要があります。 そのため、 **プリンシパル** オブジェクトを置き換える機能を必要とするアプリケーションに、プリンシパルを制御するための <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> オブジェクトを付与する必要があります。 (ロール ベースのセキュリティ チェックを実行する、または **プリンシパル** オブジェクトを作成するために、このアクセス許可は必要がないことに注意してください。)  
  
 次のタスクを実行することによって、現在の **プリンシパル** オブジェクトを置き換えることができます。  
  
1. 置き換える **プリンシパル** オブジェクトと関連付けられている **ID** オブジェクトを作成します。  
  
2. 新しい **プリンシパル** オブジェクトを呼び出しコンテキストにアタッチします。  
  
## <a name="example"></a>例  
 次の例では、汎用プリンシパル オブジェクトを作成し、それを使用してスレッドのプリンシパルを設定する方法を示します。  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [プリンシパル オブジェクトと ID オブジェクト](../../../docs/standard/security/principal-and-identity-objects.md)
