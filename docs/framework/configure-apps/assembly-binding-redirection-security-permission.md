---
title: アセンブリ バインディング リダイレクトのセキュリティ アクセス許可
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921374"
---
# <a name="assembly-binding-redirection-security-permission"></a>アセンブリ バインディング リダイレクトのセキュリティ アクセス許可
アプリケーション構成ファイルで明示的にアセンブリ バインディングをリダイレクトするには、セキュリティ アクセス許可が必要です。 これは、.NET Framework アセンブリおよびサードパーティ製アセンブリに適用されます。 権限は、 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission>にフラグを設定することによって付与されます。 マネージアセンブリには、既定ではアクセス許可がありません。  
  
 セキュリティアクセス許可は、信頼済みゾーン (ローカルコンピューター) およびイントラネットゾーンで実行されているアプリケーションに付与されます。 インターネットゾーンで実行されているアプリケーションは、アセンブリバインディングのリダイレクトを実行できません。  
  
 コンポーネントの発行元によって制御される発行者ポリシー ファイル、または管理者によって制御されるコンピューターの構成ファイルにアセンブリのリダイレクトを実行する場合は、アクセス許可は必要ありません。 ただし、アクセス許可が明示的にポリシーを使用してパブリッシャーを無視するアプリケーションに必要な[ \<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md)アプリケーション構成ファイル内の要素。  
  
 次の表は、Bindingredirects フラグの既定のセキュリティ設定を示しています。  
  
|ゾーン|BindingRedirects フラグの設定|  
|----------|-----------------------------------|  
|信頼済みゾーン (ローカルコンピューター)|**ON**|  
|イントラネットゾーン|**ON**|  
|インターネット ゾーン|**OFF**|  
|信頼されていないゾーン|**OFF**|  
  
 管理者は、これらのセキュリティ設定を変更して、特定のコンピューター上の特定のシナリオをサポートまたは制限することができます。 既定値から**Bindingredirects**フラグ設定を変更するためのツールはありません。管理者は、ユーザーのコンピューター上のセキュリティ .config ファイルを手動で編集する必要があります。  
  
## <a name="see-also"></a>関連項目

- [発行者ポリシーファイルと Side-by-side 実行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [方法: 自動バインディング リダイレクトを有効/無効にする](how-to-enable-and-disable-automatic-binding-redirection.md)
- [side-by-side 実行](../deployment/side-by-side-execution.md)
