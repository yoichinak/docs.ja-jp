---
title: ファイル モードが正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 9a59faf1b6f845858e36efcabdf0758e41ad75dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619744"
---
# <a name="bad-file-mode"></a>ファイル モードが正しくありません。
ファイルの内容を操作するために使用されるステートメントは、ファイルが開かれたモードに適している必要があります。 以下の原因が考えられます。  
  
- `FilePutObject` または `FileGetObject` ステートメントがシーケンシャル ファイルを指定しています。  
  
- `Print` ステートメントが、`Output` または `Append` 以外のアクセス モード用に開かれたファイルを指定しています。  
  
- `Input` ステートメントが、`Input` 以外のアクセス モードで開かれたファイルを指定しています  
  
- 読み取り専用ファイルに書き込もうとしました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- `FilePutObject` および `FileGetObject` が、`Random` または `Binary` アクセス用に開かれたファイルのみを参照していることを確認します。  
  
- `Print` が `Output` または `Append` アクセス モードのいずれかで開かれているファイルを指定していることを確認します。 そうでない場合は、別のステートメントを使用してファイルにデータを格納するか、適切なモードでファイルを再度開きます。  
  
- `Input` が `Input` で開かれているファイルを指定していることを確認します。 そうでない場合は、別のステートメントを使用してファイルにデータを格納するか、適切なモードでファイルを再度開きます。  
  
- 読み取り専用ファイルに書き込む場合は、ファイルの読み取り/書き込みの状態を変更するか、ファイルへの書き込みを試みないようにします。  
  
- `My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileSystem>
- [トラブルシューティング : テキスト ファイルの読み取りと書き込み](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
