---
title: '方法: アプリケーション リソースを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: 8712f7c9c60d43cf3d0348b7c3f2f4cbee0b93b1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378887"
---
# <a name="how-to-use-application-resources"></a>方法: アプリケーション リソースを使用する
この例では、アプリケーション リソースを使用する方法を示します。  
  
## <a name="example"></a>例  
 次の例は、アプリケーション定義ファイルを示しています。 アプリケーション定義ファイルがリソース セクションを定義します (値を<xref:System.Windows.Application.Resources%2A>プロパティ)。 アプリケーション レベルで定義されているリソースには、そのアプリケーションの一部であるその他すべてのページからアクセスできます。 この例では、リソースは宣言済みのスタイルです。 この例で、コントロール テンプレート内で定義されているを省略コントロール テンプレートを含む完全なスタイル指定できますが、時間がかかるため、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>スタイルのプロパティ set アクセス操作子。  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 次の例は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]前の例で定義されているアプリケーション レベルのリソースを参照するページ。 使用してリソースを参照する、 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)要求されたリソースの一意のリソース キーを指定します。 "GelButton" というキーを持つリソースが、現在のページで見つからないため、要求されているリソースのリソース ルックアップ スコープは、現在のページを越えて、定義されているアプリケーション レベルのリソースまで継続されます。  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>関連項目
- [XAML リソース](xaml-resources.md)
- [アプリケーション管理の概要](../app-development/application-management-overview.md)
- [方法トピック](resources-how-to-topics.md)
