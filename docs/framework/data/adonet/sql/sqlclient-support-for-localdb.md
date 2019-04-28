---
title: SqlClient による LocalDB のサポート
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 416945964af7fda5ed5aaab2f5aae1bbc8928556
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670054"
---
# <a name="sqlclient-support-for-localdb"></a>SqlClient による LocalDB のサポート
SQL Server コード名 Denali 以降では、LocalDB と呼ばれる SQL Server の軽量バージョンは提供されます。 このトピックでは、LocalDB データベースに接続する方法について説明します。  
  
## <a name="remarks"></a>Remarks  
 LocalDB は、LocalDB をインストールして、LocalDB インスタンスを構成する方法などの詳細については、SQL Server オンライン ブックを参照してください。  
  
 LocalDB の主な機能の概要  
  
- sqllocaldb.exe または app.config ファイルを使用して LocalDB インスタンスを作成および開始する。  
  
- sqlcmd.exe を使用して LocalDB インスタンスにデータベースを追加および変更する。 たとえば、 `sqlcmd -S (localdb)\myinst`のようにします。  
  
- `AttachDBFilename` 接続文字列キーワードを使用して LocalDB インスタンスにデータベースを追加する。 `AttachDBFilename`を使用していて、 `Database` 接続文字列キーワードでデータベースの名前を指定しない場合、アプリケーションを閉じると、データベースは LocalDB インスタンスから削除されます。  
  
- 接続文字列に LocalDB インスタンスを指定する。 たとえば、インスタンス名が `myInstance`の場合、接続文字列には次の行が含まれます。  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True` は LocalDB データベースに接続するときに使用することはできません。  
  
 LocalDB は [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065)からダウンロードできます。 Sqlcmd.exe を使用する LocalDB インスタンスのデータを変更するため、SQL Server 2012、SQL Server 2012 Feature Pack から取得することもできます。 から sqlcmd を必要があります。  
  
## <a name="programmatically-create-a-named-instance"></a>名前付きインスタンスをプログラムによって作成する  
 アプリケーションは、次のように名前付きインスタンスを作成してデータベースを指定できます。  
  
- app.config ファイルに作成するための LocalDB インスタンスを次のように指定する。  インスタンスのバージョン番号は LocalDB インストールのバージョン番号と同じである必要があります。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- `server` 接続文字列キーワードを使用してインスタンス名を指定する。  `server` 接続文字列キーワードで指定されたインスタンス名は app.config ファイルで指定された名前と一致する必要があります。  
  
- .MDF ファイルを指定するには、 `AttachDBFilename` 接続文字列キーワードを使用する。  
  
## <a name="see-also"></a>関連項目

- [SQL Server の機能と ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
