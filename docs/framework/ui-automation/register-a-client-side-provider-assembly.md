---
title: クライアント側プロバイダー アセンブリの登録
description: クライアント側 UI オートメーションプロバイダーを含む DLL を登録する方法を示す例を確認します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
ms.openlocfilehash: 034a109bb69c08883c0943b7b6ef69a397a8e7e1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168134"
---
# <a name="register-a-client-side-provider-assembly"></a>クライアント側プロバイダー アセンブリの登録
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、クライアント側 UI オートメーション プロバイダーを格納する DLL を登録する方法を説明します。  
  
## <a name="example"></a>例  
 次の例では、コンソール ウィンドウのプロバイダーを格納するアセンブリを登録する方法を示します。  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a>関連項目

- [クライアント側 UI オートメーション プロバイダーの作成](create-a-client-side-ui-automation-provider.md)
