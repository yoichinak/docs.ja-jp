---
title: ファイル モードが正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: d3d0ebd003f178567ec9e9b19d6baccb8bc15f60
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819984"
---
# <a name="bad-file-mode"></a>ファイル モードが正しくありません。
ファイルの内容を操作するときに使用するステートメントは、ファイルを開いたモードに適切なである必要があります。 以下の原因が考えられます。  
  
-   A`FilePutObject`または`FileGetObject`ステートメントがシーケンシャル ファイルを指定します。  
  
-   A`Print`ステートメント以外のアクセス モードで開かれたファイルを指定する`Output`または`Append`します。  
  
-   `Input`ステートメント以外のアクセス モードで開かれたファイルを指定します `Input`  
  
-   読み取り専用ファイルに書き込むしようとしました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   確認します`FilePutObject`と`FileGetObject`の開いているファイルを参照することはのみ`Random`または`Binary`アクセスします。  
  
-   必ず`Print`のいずれかに開かれたファイルを指定します`Output`または`Append`アクセス モード。 ない場合は、さまざまなステートメントを使用して、ファイルにデータを配置または適切なモードでファイルを再び開きます。  
  
-   必ず`Input`用に開かれたファイルを指定します`Input`します。 有効でない場合は、さまざまなステートメントを使用して、データ ファイル内に配置または適切なモードでファイルを再び開きます。  
  
-   読み取り専用ファイルを作成する場合は、ファイルの読み取り/書き込み状態を変更したりへの書き込みをしないでください。  
  
-   `My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileSystem>
- [トラブルシューティング : テキスト ファイルの読み取りと書き込み](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
