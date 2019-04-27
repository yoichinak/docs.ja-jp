---
title: インスタンス
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916397"
---
# <a name="instances"></a>インスタンス
カウンター名:インスタンス。  
  
## <a name="description"></a>説明  
 現在サービスに含まれているインスタンス コンテキストの数。  
  
 多くの場合、インスタンス コンテキストの数とインスタンスの数は同じです。 ただし、次のシナリオではこの規則は当てはまりません。  
  
-   サービス メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> メソッドを明示的に呼び出している場合。  
  
-   <xref:System.ServiceModel.ReleaseInstanceMode> が <xref:System.ServiceModel.OperationBehaviorAttribute> インスタンスに適用されている場合。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.OperationBehaviorAttribute>
