---
title: DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785350"
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
- [ADO.NET の概要](../ado-net-overview.md)
