---
title: Entity Framework 用 SqlClient の型
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: eb12bde1e319fde5adf20ad6cd54f8776aeda31d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879165"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Entity Framework 用 SqlClient の型
.NET Framework Data Provider for SQL Server (SqlClient) プロバイダー マニフェスト ファイルには、プロバイダー プリミティブ型のリスト、それぞれの型のファセット、概念モデルとストレージ モデルのプリミティブ型とのマッピング、および概念モデルとストレージ モデルのプリミティブ型間での昇格と変換の規則が含まれています。  
  
 次の表は、SQL Server 2008 では、型を示します[!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]、および[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]データベースとどのようにこれらの型マップに概念モデル型。 いくつかの新しい型が SQL Server の新しいバージョンで導入されており、これらの型は SQL Server の古いバージョンではサポートされていません。 これらの型については次の表で説明します。  
  
|プロバイダー型の<br /><br /> name|プロバイダー型の<br /><br /> 属性|`EDMSimpleType`<br /><br /> name|ファセット|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|適用なし|`Edm.Boolean`|N/A|  
|`tinyint`|N/A|`Edm.Byte`|N/A|  
|`smallint`|N/A|`Edm.Int16`|N/A|  
|`int`|N/A|`Edm.Int32`|N/A|  
|`bigint`|N/A|`Edm.Int64`|N/A|  
|`float`|N/A|`Edm.Double`|N/A|  
|`real`|N/A|`Edm.Double`|N/A|  
|`decimal`|適用なし|`Edm.Decimal`|有効桁数。<br /><br /> 最小値:1<br /><br /> 最大値:38<br /><br /> -既定値:18<br /><br /> -定数。False<br /><br /> スケール:<br /><br /> 最小値:0<br /><br /> 最大値:38<br /><br /> -既定値:0<br /><br /> -定数。False|  
|`numeric`|適用なし|`Edm.Decimal`|有効桁数。<br /><br /> 最小値:1<br /><br /> 最大値:38<br /><br /> -既定値:18<br /><br /> -定数。False<br /><br /> スケール:<br /><br /> 最小値:0<br /><br /> 最大値:38<br /><br /> -既定値:0<br /><br /> -定数。False|  
|`smallmoney`|適用なし|`Edm.Decimal`|有効桁数。<br /><br /> -既定値:10<br /><br /> -定数。True<br /><br /> スケール:<br /><br /> -既定値:4<br /><br /> -定数。True|  
|`money`|適用なし|`Edm.Decimal`|有効桁数。<br /><br /> -既定値:19<br /><br /> -定数。True<br /><br /> スケール:<br /><br /> -既定値:4<br /><br /> -定数。True|  
|`binary`|適用なし|`Edm.Binary`|MaxLength:<br /><br /> 最小値:1<br /><br /> 最大値:8000<br /><br /> -既定値:8000<br /><br /> -定数。False<br /><br /> FixedLength:<br /><br /> -既定値:True<br /><br /> -定数。True|  
|`varbinary`|適用なし|`Edm.Binary`|MaxLength:<br /><br /> 最小値:1<br /><br /> 最大値:8000<br /><br /> -既定値:8000<br /><br /> -定数。False<br /><br /> FixedLength:<br /><br /> -既定値:False<br /><br /> -定数。True|  
|`varbinary(max)`<br /><br /> メモ:この型がでサポートされていません[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]します。|適用なし|`Edm.Binary`|MaxLength:<br /><br /> -既定値:214748364780<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:False<br /><br /> -定数。True|  
|`image`|適用なし|`Edm.Binary`|MaxLength:<br /><br /> -既定値:2147483647<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:False<br /><br /> -定数。True|  
|`timestamp`|適用なし|`Edm.Binary`|MaxLength:<br /><br /> -既定値:8<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:True<br /><br /> -定数。True|  
|`rowversion`|適用なし|`Edm.Binary`|MaxLength:<br /><br /> -既定値:8<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:True<br /><br /> -定数。True|  
|`smalldatetime`|適用なし|`Edm.DateTime`|有効桁数。<br /><br /> -既定値:0<br /><br /> -定数。True|  
|`datetime`|適用なし|`Edm.DateTime`|有効桁数。<br /><br /> -既定値:3<br /><br /> -定数。True|  
|`date`<br /><br /> メモ:SQL Server 2005 および SQL Server 2000 では、この型はサポートされていません。|適用なし|`Edm.DateTime`|有効桁数。<br /><br /> -既定値:0<br /><br /> -定数。False|  
|`time`<br /><br /> メモ:SQL Server 2005 および SQL Server 2000 では、この型はサポートされていません。|適用なし|`Edm.Time`|有効桁数。<br /><br /> -既定値:7<br /><br /> -定数。False|  
|`datetime2`<br /><br /> メモ:SQL Server 2005 および SQL Server 2000 では、この型はサポートされていません。|適用なし|`Edm.DateTime`|有効桁数。<br /><br /> -既定値:7<br /><br /> -定数。False|  
|`datetimeoffset`<br /><br /> メモ:SQL Server 2005 および SQL Server 2000 では、この型はサポートされていません。|適用なし|`Edm.DateTimeOffset`|有効桁数。<br /><br /> -既定値:7<br /><br /> -定数。False|  
|`nvarchar`<br /><br /> メモ:この型がでサポートされていません[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]します。|適用なし|`Edm.String`|MaxLength:<br /><br /> 最小値:1<br /><br /> 最大値:4000<br /><br /> -既定値:4000<br /><br /> -定数。False<br /><br /> Unicode: <br /><br /> -既定値:True<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:False<br /><br /> -定数。True|  
|`varchar`<br /><br /> メモ:この型がでサポートされていません[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]します。|適用なし|`Edm.String`|MaxLength:<br /><br /> 最小値:1<br /><br /> 最大値:8000<br /><br /> -既定値:8000<br /><br /> -定数。False<br /><br /> Unicode: <br /><br /> -既定値:False<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:False<br /><br /> -定数。True|  
|`char`|適用なし|`Edm.String`|MaxLength:<br /><br /> 最小値:1<br /><br /> 最大値:8000<br /><br /> -既定値:8000<br /><br /> -定数。False<br /><br /> Unicode: <br /><br /> -既定値:False<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:True<br /><br /> -定数。True|  
|`nchar`|適用なし|`Edm.String`|MaxLength:<br /><br /> 最小値:1<br /><br /> 最大値:4000<br /><br /> -既定値:4000<br /><br /> -定数。False<br /><br /> Unicode: <br /><br /> -既定値:True<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:True<br /><br /> -定数。True|  
|`varchar`(`max`)|適用なし|`Edm.String`|MaxLength:<br /><br /> -既定値:2147483647<br /><br /> -定数。True<br /><br /> Unicode: <br /><br /> -既定値:False<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:False<br /><br /> -定数。True|  
|`nvarchar`(`max`)|適用なし|`Edm.String`|MaxLength:<br /><br /> -既定値:1073741823<br /><br /> -定数。True<br /><br /> Unicode: <br /><br /> -既定値:True<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:False<br /><br /> -定数。True|  
|`ntext`|等号比較:False<br /><br /> 順序を比較できる:False|`Edm.String`|MaxLength:<br /><br /> -既定値:1073741823<br /><br /> -定数。True<br /><br /> Unicode: <br /><br /> -既定値:False<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:False<br /><br /> -定数。True|  
|`text`|等号比較:False<br /><br /> 順序を比較できる:False|`Edm.String`|MaxLength:<br /><br /> -既定値:2147483647<br /><br /> -定数。True<br /><br /> Unicode: <br /><br /> -既定値:False<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:False<br /><br /> -定数。True|  
|`Unique`<br /><br /> `identifier`|等号比較:True<br /><br /> 順序を比較できる:True|`Edm.Guid`|適用なし|  
|`xml`|等号比較:False<br /><br /> 順序を比較できる:False|`Edm.String`|MaxLength:<br /><br /> -既定値:1073741823<br /><br /> -定数。True<br /><br /> Unicode: <br /><br /> -既定値:True<br /><br /> -定数。True<br /><br /> FixedLength:<br /><br /> -既定値:False<br /><br /> -定数。True|  
  
## <a name="see-also"></a>関連項目

- [CSDL、SSDL、および MSL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
