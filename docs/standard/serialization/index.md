---
title: シリアル化-.NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e6db24326c79ab6509b253c45c27f87a2aacd73c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053344"
---
# <a name="serialization-in-net"></a>.NET でのシリアル化

シリアル化とは、オブジェクトの状態を永続化または転送できる形式に変換するプロセスのことです。 シリアル化を補完するプロセスとして、ストリームをオブジェクトに変換する逆シリアル化があります。 これらのプロセスを一緒に使用することで、データを格納および転送できます。  
  
.NET には、次のシリアル化テクノロジがあります。  
  
- [バイナリシリアル化](binary-serialization.md)は、型の忠実性を保持します。これは、アプリケーションの異なる呼び出し間でオブジェクトの状態を保持する場合に便利です。 たとえば、クリップボードを出力先としてオブジェクトをシリアル化することによって、そのオブジェクトを異なるアプリケーション間で共有できます。 オブジェクトをシリアル化して、ストリーム、ディスク、メモリ、ネットワーク上などに出力できます。 リモート処理では、シリアル化を使用して、コンピューター間やアプリケーション ドメイン間でオブジェクトを "値渡し" します。  
  
- [XML シリアル化および SOAP シリアル化](xml-and-soap-serialization.md)では、パブリックプロパティとパブリックフィールドのみがシリアル化され、型の忠実性は維持されません。 これは、データを使用するアプリケーションに制限を加えずに、データを提供または処理する場合に有効です。 XML はオープン標準であるため、Web 経由でデータを共有する場合には有用な選択肢となります。 SOAP も同様のオープン標準であるため、有用な選択肢です。  
  
- [JSON シリアル化](system-text-json-overview.md)では、パブリックプロパティのみがシリアル化され、型の忠実性は維持されません。 JSON は、web 経由でデータを共有するための魅力的な選択肢であるオープンスタンダードです。

## <a name="reference"></a>参照

<xref:System.Runtime.Serialization>  
オブジェクトのシリアル化と逆シリアル化に使用できるクラスが含まれています。
  
<xref:System.Xml.Serialization>  
オブジェクトを XML 形式のドキュメントまたはストリームにシリアル化するために使用できるクラスが含まれています。

<xref:System.Text.Json>  
オブジェクトを JSON 形式のドキュメントまたはストリームにシリアル化するために使用できるクラスが含まれています。
