---
title: シリアル化バインダーの使用
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 10900950b935b484053fe8e37263f0dfc25eba99
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348457"
---
# <a name="usage-of-serialization-binder"></a>シリアル化バインダーの使用
このサンプルでは、<xref:System.Runtime.Serialization.SerializationBinder> を使用して、ジェネリック型のバージョンをシリアル化する際に変更する方法を示します。  
  
## <a name="demonstrates"></a>使用例  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>説明  
 このサンプルはターゲットの異なるバージョンの .NET Framework は、通信をバイナリ フォーマッタとシリアル化バインダーを使用して 2 つのエンティティを示します。  
  
このサンプルは、.NET リモート処理を使用して開発されました。 対象とするサーバーで構成されます[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]、ジェネリック型と 2 つの異なるクライアント、1 つの対象とする .NET Framework 2.0 別の対象とすると、コントラクトを実装する[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]します。  
  
 このサーバーは、シリアル化の際に型のバージョンを相応に変更できるようにするために、<xref:System.Runtime.Serialization.SerializationBinder> をバイナリ フォーマッタにアタッチします。これにより、両方のクライアントで、これらの型を適切に逆シリアル化できるようになります。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルを設定、ビルド、および実行するには  
  
1. クライアントを実行するには、SBGenericsVTS ソリューションを右クリックして (6 プロジェクト) を選び**プロパティ**します。  
  
2. **共通プロパティ**、**スタートアップ プロジェクト**を選択し、**マルチ スタートアップ プロジェクト**します。  
  
3. 選択**Server**し最初**Client20**し **[client40]** します。 選択、**開始**これら 3 つのアクションは、プロジェクトし、残りの部分に設定のままに**None**します。  
  
4. クリックして**OK**し、f5 キーを押してサンプルを実行するとします。
