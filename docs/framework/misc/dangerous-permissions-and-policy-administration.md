---
title: 危険なアクセス許可とポリシー管理
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 17a596d9fc223dc53268ae9c91f7d02357b0a9b8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489979"
---
# <a name="dangerous-permissions-and-policy-administration"></a>危険なアクセス許可とポリシー管理
.NET Framework がアクセス許可を提供する保護された操作のいくつかで、セキュリティ システムが回避されてしまう可能性があります。 これらの危険なアクセス許可は信頼できるコードにのみ付与し、その付与は必要な場合に限る必要があります。 これらのアクセス許可が付与されると、通常、悪意のあるコードに対する防御策はありません。  
  
> [!NOTE]
>  .NET Framework 4 で、.NET Framework のセキュリティ モデルと用語に重要な変更があった。 これらの変更の詳細については、次を参照してください。[セキュリティ変更](../../../docs/framework/security/security-changes.md)します。  
  
 危険なアクセス許可については、次の表で説明します。  
  
|アクセス許可|潜在的なリスク|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|マネージド コードからアンマネージド コードを呼び出せるようにしますが、これは大抵リスクを伴います。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|検証なしで、コードは何でも実行できます。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|無効な証拠でセキュリティ ポリシーをかいくぐることができます。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|セキュリティ ポリシーを変更する機能によって、セキュリティを無効にできます。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|シリアル化を使用して、ユーザー補助機能のメカニズムを回避できます。 詳細については、「 [セキュリティとシリアル化](../../../docs/framework/misc/security-and-serialization.md)」を参照してください。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|現行プリンシパルを設定する機能によって、ロール ベースのセキュリティを欺くことができます。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|スレッドにはセキュリティ状態が関連付けられているため、スレッドの操作は危険です。|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|プライベート メンバーを使用して、ユーザー補助機能のメカニズムを無効にすることができます。|  
  
## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)
