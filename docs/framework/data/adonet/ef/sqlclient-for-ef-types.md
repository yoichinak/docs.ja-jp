---
title: Entity Framework 用 SqlClient の型
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: af3a4eea08dd3f4e1a134fcb66d92bc4a3b077c7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248379"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Entity Framework 用 SqlClient の型
.NET Framework Data Provider for SQL Server (SqlClient) プロバイダー マニフェスト ファイルには、プロバイダー プリミティブ型のリスト、それぞれの型のファセット、概念モデルとストレージ モデルのプリミティブ型とのマッピング、および概念モデルとストレージ モデルのプリミティブ型間での昇格と変換の規則が含まれています。  
  
 次の表では、SQL Server 2008、SQL Server 2005、および SQL Server 2000 データベースの型と、これらの型を概念モデルの型にマップする方法について説明します。 いくつかの新しい型が SQL Server の新しいバージョンで導入されており、これらの型は SQL Server の古いバージョンではサポートされていません。 これらの型については次の表で説明します。  
  
|プロバイダー型の<br /><br /> name|プロバイダー型の<br /><br /> 属性|`EDMSimpleType`<br /><br /> name|ファセット|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|N/A|`Edm.Boolean`|N/A|  
|`tinyint`|N/A|`Edm.Byte`|N/A|  
|`smallint`|N/A|`Edm.Int16`|N/A|  
|`int`|N/A|`Edm.Int32`|N/A|  
|`bigint`|N/A|`Edm.Int64`|N/A|  
|`float`|N/A|`Edm.Double`|N/A|  
|`real`|N/A|`Edm.Double`|N/A|  
|`decimal`|N/A|`Edm.Decimal`|精度<br /><br /> 以降1<br /><br /> 個38<br /><br /> 標準18<br /><br /> 定率False<br /><br /> 段階<br /><br /> 以降0<br /><br /> 個38<br /><br /> 標準0<br /><br /> 定率False|  
|`numeric`|N/A|`Edm.Decimal`|精度<br /><br /> 以降1<br /><br /> 個38<br /><br /> 標準18<br /><br /> 定率False<br /><br /> 段階<br /><br /> 以降0<br /><br /> 個38<br /><br /> 標準0<br /><br /> 定率False|  
|`smallmoney`|N/A|`Edm.Decimal`|精度<br /><br /> 標準10<br /><br /> 定率True<br /><br /> 段階<br /><br /> 標準4<br /><br /> 定率True|  
|`money`|N/A|`Edm.Decimal`|精度<br /><br /> 標準19<br /><br /> 定率True<br /><br /> 段階<br /><br /> 標準4<br /><br /> 定率True|  
|`binary`|N/A|`Edm.Binary`|MaxLength<br /><br /> 以降1<br /><br /> 個8000<br /><br /> 標準8000<br /><br /> 定率False<br /><br /> FixedLength<br /><br /> 標準True<br /><br /> 定率True|  
|`varbinary`|N/A|`Edm.Binary`|MaxLength<br /><br /> 以降1<br /><br /> 個8000<br /><br /> 標準8000<br /><br /> 定率False<br /><br /> FixedLength<br /><br /> 標準False<br /><br /> 定率True|  
|`varbinary(max)`<br /><br /> メモ:この型は SQL Server 2000 ではサポートされていません。|N/A|`Edm.Binary`|MaxLength<br /><br /> 標準214748364780<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準False<br /><br /> 定率True|  
|`image`|N/A|`Edm.Binary`|MaxLength<br /><br /> 標準2147483647<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準False<br /><br /> 定率True|  
|`timestamp`|N/A|`Edm.Binary`|MaxLength<br /><br /> 標準8<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準True<br /><br /> 定率True|  
|`rowversion`|N/A|`Edm.Binary`|MaxLength<br /><br /> 標準8<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準True<br /><br /> 定率True|  
|`smalldatetime`|N/A|`Edm.DateTime`|精度<br /><br /> 標準0<br /><br /> 定率True|  
|`datetime`|N/A|`Edm.DateTime`|精度<br /><br /> 標準3<br /><br /> 定率True|  
|`date`<br /><br /> メモ:この型は、SQL Server 2005 および SQL Server 2000 ではサポートされていません。|N/A|`Edm.DateTime`|精度<br /><br /> 標準0<br /><br /> 定率False|  
|`time`<br /><br /> メモ:この型は、SQL Server 2005 および SQL Server 2000 ではサポートされていません。|N/A|`Edm.Time`|精度<br /><br /> 標準7<br /><br /> 定率False|  
|`datetime2`<br /><br /> メモ:この型は、SQL Server 2005 および SQL Server 2000 ではサポートされていません。|N/A|`Edm.DateTime`|精度<br /><br /> 標準7<br /><br /> 定率False|  
|`datetimeoffset`<br /><br /> メモ:この型は、SQL Server 2005 および SQL Server 2000 ではサポートされていません。|N/A|`Edm.DateTimeOffset`|精度<br /><br /> 標準7<br /><br /> 定率False|  
|`nvarchar`<br /><br /> メモ:この型は SQL Server 2000 ではサポートされていません。|N/A|`Edm.String`|MaxLength<br /><br /> 以降1<br /><br /> 個4000<br /><br /> 標準4000<br /><br /> 定率False<br /><br /> Unicode:<br /><br /> 標準True<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準False<br /><br /> 定率True|  
|`varchar`<br /><br /> メモ:この型は SQL Server 2000 ではサポートされていません。|N/A|`Edm.String`|MaxLength<br /><br /> 以降1<br /><br /> 個8000<br /><br /> 標準8000<br /><br /> 定率False<br /><br /> Unicode:<br /><br /> 標準False<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準False<br /><br /> 定率True|  
|`char`|N/A|`Edm.String`|MaxLength<br /><br /> 以降1<br /><br /> 個8000<br /><br /> 標準8000<br /><br /> 定率False<br /><br /> Unicode:<br /><br /> 標準False<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準True<br /><br /> 定率True|  
|`nchar`|N/A|`Edm.String`|MaxLength<br /><br /> 以降1<br /><br /> 個4000<br /><br /> 標準4000<br /><br /> 定率False<br /><br /> Unicode:<br /><br /> 標準True<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準True<br /><br /> 定率True|  
|`varchar`(`max`)|N/A|`Edm.String`|MaxLength<br /><br /> 標準2147483647<br /><br /> 定率True<br /><br /> Unicode:<br /><br /> 標準False<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準False<br /><br /> 定率True|  
|`nvarchar`(`max`)|N/A|`Edm.String`|MaxLength<br /><br /> 標準1073741823<br /><br /> 定率True<br /><br /> Unicode:<br /><br /> 標準True<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準False<br /><br /> 定率True|  
|`ntext`|等しい比較可能:False<br /><br /> 順序を比較する:False|`Edm.String`|MaxLength<br /><br /> 標準1073741823<br /><br /> 定率True<br /><br /> Unicode:<br /><br /> 標準False<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準False<br /><br /> 定率True|  
|`text`|等しい比較可能:False<br /><br /> 順序を比較する:False|`Edm.String`|MaxLength<br /><br /> 標準2147483647<br /><br /> 定率True<br /><br /> Unicode:<br /><br /> 標準False<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準False<br /><br /> 定率True|  
|`Unique`<br /><br /> `identifier`|等しい比較可能:True<br /><br /> 順序を比較する:True|`Edm.Guid`|N/A|  
|`xml`|等しい比較可能:False<br /><br /> 順序を比較する:False|`Edm.String`|MaxLength<br /><br /> 標準1073741823<br /><br /> 定率True<br /><br /> Unicode:<br /><br /> 標準True<br /><br /> 定率True<br /><br /> FixedLength<br /><br /> 標準False<br /><br /> 定率True|  
  
## <a name="see-also"></a>関連項目

- [CSDL、SSDL、および MSL 仕様](./language-reference/csdl-ssdl-and-msl-specifications.md)
