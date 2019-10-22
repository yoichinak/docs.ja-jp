---
title: XmlReader (System.xml) メソッド (System.xml)
author: mairaw
ms.author: mairaw
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 302be4eff32d2c96a1571d291e0b289e77694db8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582782"
---
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader Qlreader メソッド

解析のために指定されたストリーム、設定、およびコンテキスト情報を使用して、新しい <xref:System.Xml.XmlReader> インスタンスを作成します。

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>パラメーター

- `input` <xref:System.IO.Stream>  
  XML データを格納しているストリーム。

- `settings` <xref:System.Xml.XmlReaderSettings>  
  新しい <xref:System.Xml.XmlReader> インスタンスの設定。 この値は、`null` の場合もあります。

- `inputContext` <xref:System.Xml.XmlParserContext>  
  XML フラグメントの解析に必要なコンテキスト情報。 この値は、`null` の場合もあります。

## <a name="returns"></a>戻り値

<xref:System.Xml.XmlReader>  
ストリーム内の XML データの読み取りに使用するオブジェクト。

## <a name="remarks"></a>Remarks

> [!WARNING]
> @No__t_0 メソッドは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Xml>

**アセンブリ:** System.xml

**.NET Framework のバージョン:** 2.0 以降で使用できます。
