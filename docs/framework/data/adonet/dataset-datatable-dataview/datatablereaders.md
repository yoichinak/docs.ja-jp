---
title: DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1ff7868b59c6fdc4e6c443be1b831accc84f36a6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203825"
---
# <a name="datatablereaders"></a>DataTableReader
<xref:System.Data.DataTableReader> は、<xref:System.Data.DataTable> または <xref:System.Data.DataSet> の内容を、読み取り専用かつ前方参照専用の 1 つ以上の結果セットとして表します。  
  
 **Datatable**から**DataTableReader**を作成すると、結果の**DataTableReader**オブジェクトには、作成元の**datatable**と同じデータを持つ1つの結果セットが含まれます。ただし、としてマークされている行は除きます。削除. 列は、元の**DataTable**と同じ順序で表示されます。  
  
 **DataTableReader**は、を呼び出す<xref:System.Data.DataSet.CreateDataReader%2A>ことによって作成された場合、複数の結果セットを含むことができます。 結果は、**データセット**オブジェクトの<xref:System.Data.DataSet.Tables%2A>コレクション内の**datatable**と同じ順序で表示されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataReader の作成](creating-a-datareader.md)  
 **DataTableReader**オブジェクトを作成する方法について説明します。  
  
 [DataTable の移動](navigating-datatables.md)  
 **Read**メソッドを使用して、 **DataTableReader**の内容を移動する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET でのデータの取得および変更](../retrieving-and-modifying-data.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
