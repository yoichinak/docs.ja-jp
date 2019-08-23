---
title: 非同期操作
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: c104176d92667d7c8e2dc83c33bf3eb566437d7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918127"
---
# <a name="asynchronous-operations"></a>非同期操作
コマンドの実行など、データベースでの一部の操作は、完了までに長時間かかることがあります。 そのような場合、シングルスレッドのアプリケーションでは、他の操作をブロックして、コマンドが終了するまで待機しなければ操作を続行できません。 これに対して、長時間にわたる操作をバックグラウンド スレッドに割り当てることができれば、フォアグラウンド スレッドがアクティブなまま操作を続行できます。 たとえば、Windows アプリケーションでは、操作を実行中のユーザー インターフェイス スレッドの応答性を維持しながら、時間のかかる操作をバックグラウンド スレッドに委任することができます。  
  
 .NET Framework では、複数の標準的な非同期デザイン パターンが用意されており、バックグラウンド スレッドを利用して、その他の操作を完了するためにユーザー インターフェイスまたは優先順位の高いスレッドを解放できます。 ADO.NET では、<xref:System.Data.SqlClient.SqlCommand> クラスでこれらと同じデザイン パターンがサポートされています。 特に、<xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>、<xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>、および <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> メソッドと、<xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>、<xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>、および <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> メソッドとのペアによって、非同期動作がサポートされています。  
  
> [!NOTE]
> 非同期プログラミングは .NET Framework の中心的な機能であり、ADO.NET では標準のデザイン パターンが活用されます。 開発者が使用できるさまざまな非同期手法の詳細については、「[同期メソッドの非同期呼び出し](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)」を参照してください。  
  
 ADO.NET 機能での非同期技法の使用に伴う特別な考慮事項はありませんが、非同期機能は、.NET Framework のその他の領域よりも ADO.NET で使用する場合が多いと思われます。 マルチスレッドのアプリケーションは、その利点と問題点を認識した上で作成することが重要です。 このセクションに示す例は、マルチスレッド機能を組み込むアプリケーションを構築する際に考慮すべき重要な問題を提示しています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [コールバックを使用した Windows アプリケーション](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 この例では、非同期コマンドを安全に実行し、異なるスレッドのフォームと内容との対話を正しく処理する方法を示します。  
  
 [待機ハンドルを使用した ASP.NET アプリケーション](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 この例では、ASP.NET ページから複数の同時実行コマンドを実行し、すべてのコマンドの終了時に Wait ハンドルを使用して操作を管理する方法を示します。  
  
 [コンソール アプリケーションでのポーリング](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 この例では、ポーリングを使用して非同期コマンドの実行をコンソール アプリケーションで待機する方法を示します。 この技法は、クラス ライブラリまたはユーザー インターフェイスを持たないその他のアプリケーションでも有効です。  
  
## <a name="see-also"></a>関連項目

- [SQL Server と ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [同期メソッドの非同期呼び出し](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
