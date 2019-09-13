---
title: データ サービス リソースへのアクセス (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: 048cbb8708aa705fe6b03491ddfa9c107a21cda1
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894355"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>データ サービス リソースへのアクセス (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]では[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 、uri でアドレス指定できるリソースを使用してデータをフィードとして公開するためのをサポートしています。 これらのリソースは、 [Entity Data Model](../adonet/entity-data-model.md)のエンティティとリレーションシップの規則に従って表されます。 このモデルでは、エンティティはアプリケーション ドメイン内のデータの操作単位 (データ型) を表します (顧客、注文、項目、製品など)。 エンティティ データは、Representational State Transfer (REST) のセマンティクス (特に、標準的な HTTP 動詞である GET、PUT、POST、および DELETE) を使用してアクセスおよび変更できます。  
  
## <a name="addressing-resources"></a>リソースへの対処  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では、データ モデルによって公開されたデータを、URI を使用してアドレス指定します。 たとえば、次の URI は、Customers エンティティセットであるフィードを返します。これには、Customer エンティティ型のすべてのインスタンスのエントリが含まれます。  
  
```http
https://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 エンティティには、エンティティ キーという特別なプロパティがあります。 エンティティ キーは、エンティティ セット内の 1 つのエンティティを一意に識別するために使用されます。 そのため、エンティティ セット内のエンティティ型の特定のインスタンスのアドレスを指定できます。 たとえば、次の URI は、`ALFKI` のキー値のある Customer エンティティ型の特定のインスタンスのエントリを返します。  
  
```http  
https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 エンティティ インスタンスのプリミティブ プロパティおよび複合プロパティは、個別にアドレス指定することもできます。 たとえば、次の URI は特定の Customer の `ContactName` プロパティ値が含まれた XML 要素を返します。  
  
```http  
https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 前の URI に `$value` エンドポイントを含めた場合、応答メッセージにはプリミティブ プロパティの値のみが返されます。 次の例では、XML 要素のない "Maria Anders" という文字列のみが返されます。  
  
```http  
https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 エンティティ間のリレーションシップは、アソシエーションによってデータ モデル内で定義されます。 これらのアソシエーションによって、エンティティ インスタンスのナビゲーション プロパティを使用して関連エンティティをアドレス指定することが可能になります。 ナビゲーション プロパティは、単一の関連エンティティ (多対一のリレーションシップの場合) または関連エンティティのセット (一対多のリレーションシップの場合) のいずれかを返します。 たとえば、次の URI は、特定の Customer に関連付けられたすべての Orders のセットであるフィードを返します。  
  
```http  
https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 リレーションシップは通常は双方向であり、ナビゲーション プロパティのペアで表されます。 前の例で示したリレーションシップとは逆に、次の URI は特定の Order エンティティが属する Customer エンティティへの参照を返します。  
  
```http  
https://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]では、クエリ式の結果に基づいてリソースのアドレスを計算することもできます。 これにより、評価された式に基づいてリソースのセットをフィルター処理できます。 たとえば、次の URI は、リソースをフィルターして特定の Customer に 1997 年 9 月 22 日以降に出荷された Orders だけを返します。  
  
```http  
https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 詳細については[、「OData:URI 規則](https://go.microsoft.com/fwlink/?LinkId=185564)。  
  
## <a name="system-query-options"></a>System Query Options (システム クエリ オプション)  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィルター処理、並べ替え、ページングなど、リソースに対して従来のクエリ操作を実行するために使用できる一連のシステムクエリオプションを定義します。 たとえば、次の URI は、すべて`Order`のエンティティのセットと関連`Order_Detail`エンティティを返します。この場合、の末尾がで`100`はありません。  
  
```http  
https://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 返されたフィードのエントリは、注文の ShipCity プロパティの値でも並べ替えられています。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]では、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]次のシステムクエリオプションがサポートされています。  
  
|クエリ オプション|説明|  
|------------------|-----------------|  
|`$orderby`|返されるフィードのエンティティについて、既定の並べ替え順序を定義します。 次のクエリで返される Customers フィードは、国 (County) と都市 (City) で並べ替えられています。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> 詳細については[、「OData:OrderBy システムクエリオプション ($orderby)](https://go.microsoft.com/fwlink/?LinkId=186968)。|  
|`$top`|返されるフィードに含まれるエンティティの数を指定します。 次の例では、最初の 10 件の顧客をスキップし、その次の 10 件を返します。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> 詳細については[、「OData:Top システムクエリオプション ($top)](https://go.microsoft.com/fwlink/?LinkId=186969)。|  
|`$skip`|フィードにエンティティを返し始めるまでにスキップするエンティティの数を指定します。 次の例では、最初の 10 件の顧客をスキップし、その次の 10 件を返します。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> 詳細については[、「OData:システムクエリオプションをスキップします](https://go.microsoft.com/fwlink/?LinkId=186971)($skip)。|  
|`$filter`|フィードに返されるエンティティを特定の条件に基づいてフィルターする式を定義します。 このクエリ オプションは、フィルター式の評価に使用される一連の論理比較演算子、算術演算子、および定義済みクエリ関数をサポートします。 次の例は、郵便番号の末尾が 100 でないすべての注文を返します。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> 詳細については[、「OData:フィルターシステムクエリオプション ($filter)](https://go.microsoft.com/fwlink/?LinkId=186972)。|  
|`$expand`|クエリで返される関連エンティティを指定します。 関連エンティティは、クエリで返されるエンティティにフィードまたはエントリとしてインラインで含まれています。 次の例では、顧客 'ALFKI' の注文を各注文の品目の詳細と共に返します。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> 詳細については[、「OData:[システムクエリオプション ($expand)](https://go.microsoft.com/fwlink/?LinkId=186973)] を展開します。|  
|`$select`|フィードとして返されるエンティティのプロパティを指定します。 既定では、エンティティのすべてのプロパティがフィードとして返されます。 次のクエリでは、`Customer` エンティティの 3 つのプロパティが返されます。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> 詳細については[、「OData:システムクエリオプション ($select)](https://go.microsoft.com/fwlink/?LinkID=186076)を選択します。|  
|`$inlinecount`|フィードで返されるエンティティの数のカウントがフィードに含まれるように要求します。 詳細については[、「OData:Inlinecount システムクエリオプション ($inlinecount)](https://go.microsoft.com/fwlink/?LinkId=186975)。|  
  
## <a name="addressing-relationships"></a>リレーションシップのアドレス指定  
 では、エンティティセットとエンティティインスタンスをアドレス[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]指定するだけでなく、エンティティ間のリレーションシップを表すアソシエーションをアドレス指定することもできます。 この機能は、2 つのエンティティ インスタンス (Northwind サンプル データベースの注文に関連付けられた配送会社など) の間のリレーションシップを作成または変更するために必要です。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]では`$link` 、エンティティ間のアソシエーションに特に対応する演算子がサポートされています。 たとえば、次の URI を HTTP PUT 要求メッセージで指定した場合、指定した注文の配送会社を新しい配送会社に変更します。  
  
```http 
https://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 詳細については[、「OData:エントリ](https://go.microsoft.com/fwlink/?LinkId=187351)間のリンクのアドレス指定。  
  
## <a name="consuming-the-returned-feed"></a>返されたフィードの使用  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]リソースの URI を使用すると、サービスによって公開されるエンティティデータに対処できます。 Web ブラウザーの [アドレス] フィールドに URI を入力すると、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]要求されたリソースのフィード表現が返されます。 詳細については、 [WCF Data Services のクイックスタート](quickstart-wcf-data-services.md)を参照してください。 Web ブラウザーは、データサービスリソースから予想されるデータが返されることをテストする場合に便利ですが、データの作成、更新、および削除を行うことができる運用データサービスは、通常、Web ページのアプリケーションコードまたはスクリプト言語によってアクセスされます。 詳細については、「[クライアントアプリケーションでのデータサービスの使用](using-a-data-service-in-a-client-application-wcf-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Open Data Protocol Web サイト](https://go.microsoft.com/fwlink/?LinkID=182204)
