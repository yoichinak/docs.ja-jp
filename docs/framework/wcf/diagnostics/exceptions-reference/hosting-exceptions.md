---
title: ホスティング例外
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934733"
---
# <a name="hosting-exceptions"></a>ホスティング例外
ここでは、ホスティングによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|完全 URI は許可されていません。 完全 URI は、ServiceHostingEnvironment.EnsureServiceAvailable API に対しては許可されていません。 対応するサービスの仮想パスを使用してください。|  
|Hosting_BuildProviderCouldNotCreateType|指定した CLR 型をサービスのコンパイル中に読み込むことができません。 この型がいずれか、アプリケーションのあるソース ファイルで定義されていることを確認\\\App_Code ディレクトリにあるアプリケーションのコンパイル済みのアセンブリに含まれている\\\bin ディレクトリ、またはにインストールされているアセンブリに存在しますグローバル アセンブリ キャッシュです。 型名では、大文字と小文字が区別されます。 などのディレクトリ\\\App_Code と\\\bin は、アプリケーションのルート ディレクトリに配置する必要があります。 \\\App_Code と\\\bin ディレクトリをサブディレクトリで入れ子にすることはできません。|
