---
title: モデリングとマッピング
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 847d518710b21df714343b541401ff7fc8443fb3
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828307"
---
# <a name="modeling-and-mapping"></a>モデリングとマッピング
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、概念モデル、ストレージ モデル、およびこの 2 つのモデル間のマッピングをアプリケーションに最適な方法で定義できます。 Visual Studio で Entity Data Model ツールは、作成することができます。[edmx ファイル](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))からデータベースまたはグラフィカルなモデルと、更新、データベースまたはモデルが変更されたときにファイルをします。  
  
 Entity Framework 4.1 以降では、Code First の開発を使用してモデルをプログラムで作成することもできます。 Code First の開発に対しては、2 つの異なるシナリオがあります。 どちらの場合でも、開発者は .NET Framework のクラス定義をコーディングしてモデルを定義し、データ注釈または Fluent API を使用してオプションで追加のマッピングまたは構成を指定します。  
  
 詳細については、[概念モデルのマッピングの作成と](https://go.microsoft.com/fwlink/?LinkId=235016)を参照してください。  
  
 含まれている EDM ジェネレーターを使用することも、[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]します。 EdmGen.exe は、既存のデータ ソースから .csdl ファイル、.ssdl ファイル、および .msl ファイルを生成します。 モデルとマッピングの内容を手動で作成することもできます。 詳細については、[EDM ジェネレーター (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)を参照してください。
