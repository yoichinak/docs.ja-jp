---
title: 移行に関する注意事項 (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: b6224dcf883daef7b35ef50b7556fc568e433a46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310422"
---
# <a name="migration-considerations-entity-framework"></a>移行に関する注意事項 (Entity Framework)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework には、既存のアプリケーションにとっていくつかの利点があります。 特に重要な利点の 1 つが、概念モデルを使用して、アプリケーションで使用するデータ構造をデータ ソースのスキーマから分離できることです。 これにより、ストレージ モデルやデータ ソース自体の将来の変更が容易になり、その変更を補うための変更をアプリケーションに加える必要がなくなります。 使用する利点の詳細については、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]を参照してください[Entity Framework の概要](../../../../../docs/framework/data/adonet/ef/overview.md)と[Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)します。  
  
 利点を活用するために、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]、既存のアプリケーションを移行することができます、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]します。 移行作業の一部はすべてのアプリケーションに共通です。 これらの一般的なタスクには、使用するアプリケーションのアップグレードが含まれて、[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]バージョン 3.5 Service Pack 1 (SP1) 以降、モデルの定義、マッピング、および Entity Framework を構成します。 そのほか、アプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行する際には、 移行するアプリケーションの種類やアプリケーションの特定の機能に依存する注意点もあります。 このトピックでは、既存のアプリケーションをアップグレードする際に最適な方法を選択するために役立つ情報を紹介します。  
  
## <a name="general-migration-considerations"></a>全般的な移行の注意点  
 アプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行する際には次の点に注意してください。  
  
-   使用するアプリケーション、 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] version 3.5 SP1 以降に移行できる、Entity Framework アプリケーションで使用されるデータ ソースのデータ プロバイダーは、Entity Framework をサポートしている限り、します。  
  
-   データ ソース プロバイダーが Entity Framework をサポートしていても、そのプロバイダーのすべての機能が Entity Framework でサポートされるとは限りません。  
  
-   大規模なアプリケーションや複雑なアプリケーションの場合、アプリケーション全体を一度に Entity Framework に移行する必要はありません。 ただし、Entity Framework を使用しない部分がアプリケーションにある場合、それらの部分については、データ ソースが変更された場合に変更が必要になります。  
  
-   [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] データ プロバイダーを使用してデータ ソースにアクセスするため、Entity Framework が使用するデータ プロバイダー接続をアプリケーションの他の部分と共有できます  (たとえば、Entity Framework は SqlClient プロバイダーを使用して SQL Server データベースにアクセスします)。 詳細については、次を参照してください。 [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)します。  
  
## <a name="common-migration-tasks"></a>共通の移行タスク  
 既存アプリケーションの [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] への移行パスは、アプリケーションの種類と既存のデータ アクセス計画の両方に依存します。 ただし、以下のタスクは、既存のアプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行する際に常に実行する必要があります。  
  
> [!NOTE]
>  Visual Studio 2008 以降で Entity Data Model ツールを使用する場合は、自動的に実行これらすべてのタスク。 詳細については、「[方法 :エンティティ データ モデル ウィザードを使用して](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))します。  
  
1. アプリケーションをアップグレードします。  
  
     Visual Studio の以前のバージョンを使用して作成されたプロジェクトと[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]使用して、Visual Studio 2008 SP1 にアップグレードする必要があります、 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] version 3.5 SP1 以降します。  
  
2. モデルおよびマッピングを定義します。  
  
     モデル ファイルとマッピング ファイルでは、概念モデルのエンティティ、データ ソースの構造 (テーブル、ストアド プロシージャ、ビューなど)、およびエンティティとデータ ソース構造との間のマッピングを定義します。 詳細については、「[方法 :モデルを定義して、マッピング ファイルを手動で](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))します。  
  
     ストレージ モデルに定義されている型は、データ ソースのオブジェクトと名前が一致している必要があります。 また、既存のアプリケーションでデータがオブジェクトとして公開されている場合は、概念モデルに定義するエンティティおよびプロパティの名前を既存のデータ クラスおよびプロパティの名前に一致させる必要があります。 詳細については、「[方法 :モデリング ファイルとマッピング ファイルをカスタム オブジェクトを操作するカスタマイズ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100))します。  
  
    > [!NOTE]
    >  Entity Data Model デザイナーを使用すると、概念モデルのエンティティの名前を既存のオブジェクトに合わせて変更できます。 詳細については、次を参照してください。 [Entity Data Model デザイナー](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100))します。  
  
3. 接続文字列を定義します。  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] で概念モデルに対してクエリを実行する際には特殊な形式の接続文字列を使用します。 この接続文字列は、モデル ファイルとマッピング ファイルに関する情報とデータ ソースへの接続に関する情報をカプセル化したものです。 詳細については、「[方法 :接続文字列を定義](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)します。  
  
4. Visual Studio プロジェクトを構成します。  
  
     参照[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]アセンブリおよびモデルとマッピング ファイルは、Visual Studio プロジェクトに追加する必要があります。 これらのマッピング ファイルをプロジェクトに追加することで、接続文字列で指定された場所にアプリケーションと共に配置されるようにすることができます。 詳細については、「[方法 :Entity Framework プロジェクトを手動で構成](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))します。  
  
## <a name="considerations-for-applications-with-existing-objects"></a>既存のオブジェクトを含むアプリケーションの注意点  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4 以降では、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は POCO ("plain old" CLR object、永続化非依存オブジェクトとも呼ばれます) をサポートしています。 ほとんどの場合、既存のオブジェクトを少し変更すれば [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] で使用できます。 詳細については、次を参照してください。 [POCO エンティティの操作](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100))します。 アプリケーションを移行することも、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]と Entity Framework ツールによって生成されるデータ クラスを使用します。 詳細については、「[方法 :エンティティ データ モデル ウィザードを使用して](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))します。  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>ADO.NET プロバイダーを使用するアプリケーションの注意点  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] SqlClient などのプロバイダーでは、表形式のデータを返すデータ ソースのクエリを有効にします。 データを読み込むことも、[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]データセット。 以下は、既存の [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] プロバイダーを使用するアプリケーションをアップグレードする場合の注意点です。  
  
- データ リーダーを使用して表形式のデータを表示している場合  

  実行を検討してください、[!INCLUDE[esql](../../../../../includes/esql-md.md)]クエリ EntityClient プロバイダーを使用して、返された反復<xref:System.Data.EntityClient.EntityDataReader>オブジェクト。 この方法を使用するのは、データ リーダーを使用して表形式のデータを表示するアプリケーションで、データをオブジェクトに具体化したり、変更を追跡したり、更新を行ったりするための [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] の機能が不要である場合だけにしてください。 データ ソースを更新する既存のデータ アクセス コードも引き続き使用できますが、<xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> の <xref:System.Data.EntityClient.EntityConnection> プロパティから既存の接続にアクセスできます。 詳細については、次を参照してください。 [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)します。  
  
- DataSet を使用している場合  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]メモリ内の永続化など、DataSet によって提供される機能の多くの変更追跡、データ バインディング、および XML データとしてオブジェクトをシリアル化を提供します。 詳細については、次を参照してください。[オブジェクトの操作](../../../../../docs/framework/data/adonet/ef/working-with-objects.md)します。  
  
  場合、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 、機能は提供されません、アプリケーションに必要なデータセットのことができますも活用する LINQ クエリのメリットを使用して[!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]します。 詳細については、「[LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>データをコントロールにバインドするアプリケーションの注意点  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] DataSet やなどのデータ ソース内でデータをカプセル化できる[!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]データのソース管理、およびそれらのデータ コントロールをユーザー インターフェイス要素をバインドします。 以下は、コントロールを Entity Framework データにバインドする場合の注意点です。  
  
- コントロールへのデータ バインディング  

  概念モデルを照会するときに、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]エンティティ型のインスタンスであるオブジェクトとしてデータを返します。 これらのオブジェクトは、コントロールに直接バインドすることができ、このバインディングは、更新プログラムをサポートします。 内の行などのコントロールにデータを変更することを意味、 <xref:System.Windows.Forms.DataGridView>、自動的にデータベースに保存時に、<xref:System.Data.Objects.ObjectContext.SaveChanges%2A>メソッドが呼び出されます。  
  
  クエリの結果を列挙して、データ バインディングをサポートする <xref:System.Windows.Forms.DataGridView> などのコントロールにデータを表示するアプリケーションは、そのコントロールを <xref:System.Data.Objects.ObjectQuery%601> の結果にバインドするように変更できます。  
  
  詳細については、次を参照してください。[コントロールへのオブジェクトのバインド](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100))します。  
  
- [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] データ ソース コントロール  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]でのデータ バインディングを容易にデータ ソース コントロールが含まれています[!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]Web アプリケーション。 詳細については、次を参照してください。 [EntityDataSource Web サーバー コントロールの概要](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100))します。  
  
## <a name="other-considerations"></a>その他の注意事項  
 以下は、特定の種類のアプリケーションを Entity Framework に移行する場合の注意点です。  
  
- データ サービスを公開するアプリケーション  

  Windows Communication Foundation (WCF) をベースとする Web サービスやアプリケーションは、XML 要求/応答メッセージ形式を使用して基になるデータ ソースのデータを公開します。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、バイナリ、XML、または WCF データ コントラクトのシリアル化を使用してエンティティ オブジェクトをシリアル化できます。 バイナリ シリアル化と WCF シリアル化ではオブジェクト グラフの完全なシリアル化がサポートされています。 詳細については、次を参照してください。 [N 層アプリケーションの構築](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100))します。  
  
- XML データを使用するアプリケーション  

  オブジェクトのシリアル化では、作成することができます[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]データ サービス。 XML データを使用するアプリケーション (AJAX ベースのインターネット アプリケーションなど) にデータを提供する  データ サービスを作成できます。 このような場合は [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)] の使用を検討してください。 これらのデータ サービスは、エンティティ データ モデルに基づいて、標準の Representational State Transfer (REST) HTTP アクションを使用してエンティティ データへの動的アクセスを提供しなど、GET、PUT、および投稿をします。 詳細については、「[WCF Data Services 4.5](../../../../../docs/framework/data/wcf/index.md)」を参照してください。  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] はネイティブ XML データ型をサポートしていません。 そのため、XML 列を持つテーブルにエンティティをマップすると、その XML 列に対応するエンティティ プロパティは文字列になります。 このような場合は、オブジェクトを切断して XML としてシリアル化することができます。 詳細については、次を参照してください。[オブジェクトのシリアル化](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100))します。  
  
  アプリケーションで XML データのクエリ機能が必要な場合も、LINQ to XML を使用して LINQ クエリを活用することができます。 詳細については、次を参照してください。 [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)または[LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)します。  
  
- 状態を保持するアプリケーション  

  [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Web アプリケーションは、Web ページまたはユーザー セッションの状態を維持頻繁にする必要があります。 内のオブジェクト、<xref:System.Data.Objects.ObjectContext>インスタンスまたはサーバーで、セッション状態、クライアントのビュー ステートに格納し、後で取得して新しいオブジェクト コンテキストに再アタッチします。 詳細については、次を参照してください。[のアタッチとデタッチ オブジェクト](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100))します。  
  
## <a name="see-also"></a>関連項目

- [配置に関する注意事項](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Entity Framework の用語](../../../../../docs/framework/data/adonet/ef/terminology.md)
