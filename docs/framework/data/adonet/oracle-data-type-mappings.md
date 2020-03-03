---
title: Oracle データ型のマッピング
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: be478741069e9edd406d73c0b75d5960b9909896
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783425"
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
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型は、**数値**データ型の別名であり、が浮動小数点値<xref:System.Data.OracleClient.OracleDataReader>ではなく、 **Decimal**また<xref:System.Data.OracleClient.OracleNumber>はを返すように設計されています。 .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型は、**数値 (38)** データ型の別名であり、が**Decimal**または<xref:System.Data.OracleClient.OracleNumber>整数<xref:System.Data.OracleClient.OracleDataReader>値の代わりにを返すように設計されています。 .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**年から月までの期間**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**間隔の1秒間**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**長生**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**少数**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|.NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF カーソル**|||Oracle **REF CURSOR**データ型は、 <xref:System.Data.OracleClient.OracleDataReader>オブジェクトではサポートされていません。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ローカルタイムゾーンを使用したタイムスタンプ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**タイムゾーンを使用したタイムスタンプ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**符号なし整数**|**数値**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型は、**数値 (38)** データ型の別名であり、では、符号なし<xref:System.Data.OracleClient.OracleDataReader>整数値ではなく、 <xref:System.Data.OracleClient.OracleNumber> **Decimal**またはを返すように設計されています。 .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 次の表に、Oracle のデータ型と、**それらをパラメーター**としてバインドする<xref:System.Data.OracleClient.OracleType>ときに使用する .NET Framework データ型 (system.string および) を示します。  
  
|Oracle データ型|パラメーターとしてバインドする DbType 列挙型|パラメーターとしてバインドする OracleType 列挙型|Remarks|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle で**は、bfile パラメーターと**してのみ、 **bfile**をバインドできます。 .NET Data Provider for Oracle では、 **byte []** や<xref:System.Data.OracleClient.OracleBinary>など、**BFILE**以外の値をバインドしようとしても、自動的には作成されません。|  
|**BLOB**||**Blob**|Oracle では blob を**blob**パラメーターと**してバインド**できます。 .NET Data Provider for Oracle では、 **byte []** や<xref:System.Data.OracleClient.OracleBinary>など、**BLOB**以外の値をバインドしようとしても、自動的には作成されません。|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle では、clob を**clob**パラメーターと**してのみ**バインドできます。 .NET Data Provider for Oracle では、 **system.string**や<xref:System.Data.OracleClient.OracleString>などの**CLOB**以外の値をバインドしようとしても、自動的には作成されません。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、Double、Decimal**|**Float、Double、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>system.string <xref:System.Data.OracleClient.OracleType>と**を指定します**。|  
|**INTEGER**|**SByte、Int16、Int32、Int64、Decimal**|**SByte、Int16、Int32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>system.string <xref:System.Data.OracleClient.OracleType>と**を指定します**。|  
|**年から月までの期間**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**間隔の1秒間**|**Object**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**長生**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle では、 **NCLOB**パラメーターとして**NCLOB**をバインドすることのみできます。 .NET Data Provider for Oracle では、 **system.string**や<xref:System.Data.OracleClient.OracleString>など、**NCLOB**以外の値をバインドしようとしても、自動的には作成されません。|  
|**少数**|**VarNumeric**|**数値**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**Binary**|**素材**||  
|**REF カーソル**||**G**|詳細については、「 [Oracle REF cursor](oracle-ref-cursors.md)」を参照してください。|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**タイムスタンプ**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**ローカルタイムゾーンを使用したタイムスタンプ**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**タイムゾーンを使用したタイムスタンプ**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**符号なし整数**|**Byte、UInt16、UInt32、UInt64、Decimal**|**Byte、UInt16、Uint32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>system.string <xref:System.Data.OracleClient.OracleType>と**を指定します**。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 <xref:System.Data.OracleClient.OracleParameter>オブジェクトのプロパティ<xref:System.Data.OracleClient.OracleParameter.Value%2A>で使用される InputOutput、 **Output** **、および** **ParameterDirection**値は、入力値が Oracle データ型 (の場合) でない限り、データ型 .NET Framework ます。たとえば、 <xref:System.Data.OracleClient.OracleNumber>また<xref:System.Data.OracleClient.OracleString>は) を使用します。 これは、 **REF CURSOR**、 **BFILE**、または**LOB**データ型には適用されません。  
  
## <a name="see-also"></a>関連項目

- [Oracle および ADO.NET](oracle-and-adonet.md)
- [ADO.NET の概要](ado-net-overview.md)
