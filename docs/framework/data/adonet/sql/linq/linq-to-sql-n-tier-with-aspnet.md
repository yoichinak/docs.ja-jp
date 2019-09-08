---
title: ASP.NET での LINQ to SQL N 層
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1770d84053b57e05d1a4e41919a3eb4122dc73a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793028"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>ASP.NET での LINQ to SQL N 層
を使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]する ASP.NET アプリケーションでは、 <xref:System.Web.UI.WebControls.LinqDataSource> Web サーバーコントロールを使用します。 このコントロールは、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]に対するクエリ実行、ブラウザーへのデータ送信、データの取得、データベースを更新する [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> へのデータ送信など、必要なほとんどのロジックを扱います。 マークアップでこのコントロールを構成するだけで、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] とブラウザーの間のすべてのデータ転送をコントロールが処理するようになります。 コントロールはプレゼンテーション層との対話を処理し、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]データ層との通信を処理するので、ASP.NET 多層アプリケーションの主な目的は、カスタムビジネスロジックを作成することです。  
  
 の詳細`LINQDataSource`については、「 [LinqDataSource Web サーバーコントロールの概要](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション](n-tier-and-remote-applications-with-linq-to-sql.md)
