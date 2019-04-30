---
ms.openlocfilehash: f01d0a24202ecda7e23cbe925bb6dc8962cb7574
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750726"
---
> [!CAUTION]
>  コード アクセス セキュリティと部分的に信頼できるコード  
>   
>  .NET Framework には、コード アクセス セキュリティ (CAS) と呼ばれる、同一アプリケーションで実行される各種コードにさまざまな信頼レベルを強制的に適用するメカニズムが備わっています。  .NET Framework のコード アクセス セキュリティは、コードの実行元や他の ID 情報に基づいてセキュリティ境界を適用するメカニズムとして使用しないでください。 現在、部分的に信頼されるコード (特に実行元が不明なコード) では、コード アクセス セキュリティと透過的セキュリティ コードがセキュリティ境界としてサポートされないように、ガイダンスを更新しています。 発生元の不明なコードの読み込みと実行に関しては、他のセキュリティ対策を適切に導入することなく行わないようにしてください。  
>   
>  このポリシーは .NET Framework のすべてのバージョンに適用されますが、Silverlight に含まれる .NET Framework には適用されません。