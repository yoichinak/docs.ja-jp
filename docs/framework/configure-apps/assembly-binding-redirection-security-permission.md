---
title: アセンブリ バインディング リダイレクトのセキュリティ アクセス許可
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: ba4e7e790860696f4489e9ef7b73bddcb8c4e399
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705429"
---
# <a name="assembly-binding-redirection-security-permission"></a>アセンブリ バインディング リダイレクトのセキュリティ アクセス許可
アプリケーション構成ファイルで明示的にアセンブリ バインディングをリダイレクトするには、セキュリティ アクセス許可が必要です。 これは、.NET Framework アセンブリおよびサードパーティ製アセンブリに適用されます。 許可を設定して、<xref:System.Security.Permissions.SecurityPermissionFlag>にフラグ、<xref:System.Security.Permissions.SecurityPermission>します。 マネージ アセンブリは、既定でアクセス許可を持っていません。  
  
 セキュリティ アクセス許可は、イントラネット ゾーン、信頼済みゾーン (ローカル コンピューター) で実行されるアプリケーションに付与されます。 インターネット ゾーンで実行されているアプリケーションが、アセンブリ バインド リダイレクトを実行するから固く禁止されています。  
  
 コンポーネントの発行元によって制御される発行者ポリシー ファイル、または管理者によって制御されるコンピューターの構成ファイルにアセンブリのリダイレクトを実行する場合は、アクセス許可は必要ありません。 ただし、アクセス許可が明示的にポリシーを使用してパブリッシャーを無視するアプリケーションに必要な[ \<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)アプリケーション構成ファイル内の要素。  
  
 次の表は、既定のセキュリティ設定、 **BindingRedirects**フラグ。  
  
|ゾーン|BindingRedirects フラグの設定|  
|----------|-----------------------------------|  
|信頼済みゾーン (ローカル コンピューター)|**ON**|  
|イントラネット ゾーン|**ON**|  
|インターネット ゾーン|**OFF**|  
|信頼されていないゾーン|**OFF**|  
  
 管理者は、これらのセキュリティ設定をサポートしたり、特定のコンピューターで特定のシナリオの制限を変更できます。 変更するためのツールはありません、 **BindingRedirects**フラグ設定から既定では、管理者はユーザーのコンピューターに Security.config ファイルを編集する必要があります手動でします。  
  
## <a name="see-also"></a>関連項目

- [発行者ポリシー ファイルとサイド バイ サイドで実行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [方法: 自動バインディング リダイレクトを有効/無効にする](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [side-by-side 実行](../../../docs/framework/deployment/side-by-side-execution.md)
