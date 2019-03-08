---
title: XML からのデータ型クラスの生成
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: a6666f1ba23dd563bd7a005d458cd7fe8253c3af
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679087"
---
# <a name="generating-data-type-classes-from-xml"></a>XML からのデータ型クラスの生成
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] には、XML からデータ型クラスを生成するための新しい機能があります。 このトピックでは、.NET ブログ RSS フィードのデータ型を自動的に生成する方法について説明します。  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>フィードから .NET ブログの RSS XML を取得します。  
  
1.  Internet Explorer に移動します。、 [.NET ブログの RSS フィード](https://devblogs.microsoft.com/dotnet/feed/)します。  
  
2.  ページを右クリックして**ソースの表示**します。  
  
3.  キーを押してフィードのテキストをコピー **Ctrl + A**すべてのテキストを選択して**Ctrl + C**にコピーします。  
  
### <a name="creating-the-data-types"></a>データ型の作成  
  
1.  プロキシが使用されるコード ファイルを開きます。 このファイルは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] プロジェクトの一部である必要があります。  
  
2.  既存のクラスの外部にあるファイルの場所にカーソルを置きます。  
  
3.  選択**編集**、**ペースト**、 **XML をクラスとして貼り付ける**します。  
  
4.  クラスと呼ばれる`link`、 `rss`、 `rssChannel`、 `rssChannelImage`、`rssChannelItem`と`rssChannelItemGuid`RSS フィード内の要素にアクセスするために必要なメンバーで作成されます。  
  
### <a name="using-the-generated-classes"></a>生成されたクラスの使用  
  
1.  クラスが生成されると、他のクラスのコードなどで使用できます。 次のコード例では、`rssChannelImage` クラスの新しいインスタンスが返されます。  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
