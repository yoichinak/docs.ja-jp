---
title: Oracle データ型のマッピング
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: d5e13b0ff4f9c3d5cc145abd4f0bcc3d8e717ca1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965772"
---
# <a name="oracle-data-type-mappings"></a>Oracle データ型のマッピング
次の表に、Oracle データ型およびその <xref:System.Data.OracleClient.OracleDataReader> へのマップを示します。  
  
|Oracle データ型|OracleDataReader.GetValue によって返される .NET Framework データ型|OracleDataReader.GetOracleValue によって返される OracleClient データ型|Remarks|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型のエイリアスでは、**数**データ型とは、ように、<xref:System.Data.OracleClient.OracleDataReader>を返します、 **System.Decimal**または<xref:System.Data.OracleClient.OracleNumber>浮動小数点値ではなく。 .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型のエイリアスでは、 **NUMBER(38)** データ型とは、ように、<xref:System.Data.OracleClient.OracleDataReader>を返します、 **System.Decimal**または<xref:System.Data.OracleClient.OracleNumber>整数値ではなく。 .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**2 番目の間隔の日**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**数**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|.NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR**では、データ型はサポートされていない、<xref:System.Data.OracleClient.OracleDataReader>オブジェクト。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ローカル タイム ゾーンのタイムスタンプ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**タイム ゾーンのタイムスタンプ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**符号なし整数**|**数値**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型のエイリアスでは、 **NUMBER(38)** データ型とは、ように、<xref:System.Data.OracleClient.OracleDataReader>を返します、 **System.Decimal**または<xref:System.Data.OracleClient.OracleNumber>符号なし整数値ではなく。 .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 次の表は、Oracle データ型と .NET Framework データ型 (**System.Data.DbType**と<xref:System.Data.OracleClient.OracleType>) パラメーターとしてバインドするときに使用します。  
  
|Oracle データ型|パラメーターとしてバインドする DbType 列挙型|パラメーターとしてバインドする OracleType 列挙型|Remarks|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle では、バインドのみが許可、 **BFILE**として、 **BFILE**パラメーター。 .NET Data Provider for Oracle はいない自動的に構築すること以外にバインドしようとした場合**BFILE**などの値**byte[]** または<xref:System.Data.OracleClient.OracleBinary>します。|  
|**BLOB**||**Blob**|Oracle では、バインドのみが許可、 **BLOB**として、 **BLOB**パラメーター。 .NET Data Provider for Oracle はいない自動的に構築すること以外にバインドしようとした場合**BLOB**などの値**byte[]** または<xref:System.Data.OracleClient.OracleBinary>します。|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle では、バインドのみが許可、 **CLOB**として、 **CLOB**パラメーター。 .NET Data Provider for Oracle はいない自動的に構築すること以外にバインドしようとした場合**CLOB**などの値**System.String**または<xref:System.Data.OracleClient.OracleString>します。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、Double、Decimal**|**Float、Double、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定、 **System.Data.DBType**と<xref:System.Data.OracleClient.OracleType>します。|  
|**INTEGER**|**SByte、Int16、Int32、Int64、Decimal**|**SByte、Int16、Int32、Number します。**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定、 **System.Data.DBType**と<xref:System.Data.OracleClient.OracleType>します。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**2 番目の間隔の日**|**Object**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle では、バインドのみが許可、 **NCLOB**として、 **NCLOB**パラメーター。 .NET Data Provider for Oracle はいない自動的に構築すること以外にバインドしようとした場合**NCLOB**などの値**System.String**または<xref:System.Data.OracleClient.OracleString>します。|  
|**数**|**VarNumeric**|**数値**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**Binary**|**生**||  
|**REF CURSOR**||**カーソル**|詳細については、次を参照してください。 [Oracle REF Cursor](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)します。|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**タイムスタンプ**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**ローカル タイム ゾーンのタイムスタンプ**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**タイム ゾーンのタイムスタンプ**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**符号なし整数**|**Byte、UInt16、UInt32、UInt64、Decimal**|**Byte、UInt16、Uint32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 決定、 **System.Data.DBType**と<xref:System.Data.OracleClient.OracleType>します。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **InputOutput**、**出力**、および**ReturnValue** **ParameterDirection**によって使用される値、 <xref:System.Data.OracleClient.OracleParameter.Value%2A> のプロパティ<xref:System.Data.OracleClient.OracleParameter>入力値が、Oracle のデータ型でない限り、オブジェクトは、.NET Framework データ型 (たとえば、<xref:System.Data.OracleClient.OracleNumber>または<xref:System.Data.OracleClient.OracleString>)。 これには適用されません**REF CURSOR**、 **BFILE**、または**LOB**データ型。  
  
## <a name="see-also"></a>関連項目
- [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
