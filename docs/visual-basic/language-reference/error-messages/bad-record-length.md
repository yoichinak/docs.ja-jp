---
title: レコード長が正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 7ec0a8c27f425ec717bca5d45d5dfd2b601c11d5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665736"
---
# <a name="bad-record-length"></a>レコード長が正しくありません。
このエラーでは以下の原因が考えられます。  
  
- 指定されたレコードの変数の長さ、 `FileGet`、 `FileGetObject`、`FilePut`または`FilePutObject`ステートメントは、対応する指定された長さによって異なります。`FileOpen`ステートメント。  
  
- 内の変数を`FilePut`または`FilePutObject`ステートメントまたは可変長文字列が含まれています。  
  
- 内の変数を`FilePut`または`FilePutObject`かが含まれています、`Variant`型。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 記載されている値と同じレコードの変数の型を定義するユーザー定義型の変数を固定長のサイズの合計がかどうかを確認、`FileOpen`ステートメントの`Len`句。  
  
2. 場合に、変数、`FilePut`または`FilePutObject`ステートメントが可変長文字列が含まれるか、可変長文字列が少なくとも 2 つの文字で指定されたレコードの長さよりも短いかどうかを確認、`Len`の句、 `FileOpen`ステートメント。  
  
3. 場合内の変数を`FilePut`または`FilePutObject`かが含まれています、`Variant`可変長文字列は、少なくとも 4 バイトで指定されたレコードの長さよりも短いかどうかを確認、`Len`の句、`FileOpen`ステートメント。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
