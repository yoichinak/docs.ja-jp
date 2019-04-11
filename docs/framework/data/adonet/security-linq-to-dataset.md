---
title: セキュリティ (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: aa281cb4d6019ca2df85137eb505724e55b8060a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087337"
---
# <a name="security-linq-to-dataset"></a>セキュリティ (LINQ to DataSet)
このトピックでは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] におけるセキュリティの問題について説明します。  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>信頼できないコンポーネントへのクエリの受け渡し  
 A[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリをプログラムの 1 つのポイントを使って作成し、別のアカウントで実行します。 このクエリは、それが定義されている場所から見えるすべての要素、たとえば、呼び出し元のメソッドが所属しているクラスのプライベート メンバーやローカル変数/引数を表すシンボルなどを参照できます。 実行時には、呼び出し元のコードから見えなくても、クエリの定義時に参照されたメンバーであれば、事実上アクセスできることになります。 クエリを実行するコードが、任意に見える要素を増やすことはできません。つまり、アクセスできる範囲を実行元のコードそのものが決めることはできません。 アクセスの範囲は、クエリがアクセスできる範囲に限定されており、そのクエリ自体を通してのみアクセスできます。  
  
 つまり、クエリへの参照をコードの別の部分に渡した場合、そのクエリを受け取ったコンポーネントが信頼され、パブリックであるか、プライベートであるかに関係なく、クエリによって参照されたすべてのメンバーに対するアクセスが許可されます。 一般に、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリが慎重に構築された情報をプライベートに保持する必要がありますは公開されませんようにしない限り、クエリを信頼されていないコンポーネントに渡されませんする必要があります。  
  
## <a name="external-input"></a>外部入力  
 アプリケーションによっては (ユーザーや他の外部エージェントからの) 外部入力を受け取り、その入力内容に応じた処理を実行する場合があります。  場合[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]アプリケーションは、特定の方法で、外部入力または使用して外部のクエリの入力に基づいてクエリを構築可能性があります。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリでは、リテラルを受け入れるようにすべての場所でパラメーターを受け入れます。 アプリケーションの開発者は、外部エージェントから受け取ったリテラルを直接クエリに挿入することは避け、パラメーター化クエリを使用するようにしてください。  
  
 直接、間接を問わず、ユーザーまたは外部エージェントから受け取った入力には、対象言語の構文を巧みに利用して不正なアクションを実行する内容が含まれている可能性があります。 これは、対象言語が Transact-SQL である場合、その攻撃パターンにちなんで SQL インジェクション攻撃と呼ばれます。 クエリに直接挿入されるユーザー入力を使用して、データベースのテーブルを削除したり、サービス拒否の状態を引き起こしたり、本来実行される操作を改変したりします。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 内でクエリを構築することは可能ですが、オブジェクト モデルの API を介して構築します。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリは、Transact sql ではその意味で SQL インジェクション攻撃を受けやすくない文字列操作や文字列連結を使用して、構成されていません。  
  
## <a name="see-also"></a>関連項目

- [プログラミング ガイド](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
