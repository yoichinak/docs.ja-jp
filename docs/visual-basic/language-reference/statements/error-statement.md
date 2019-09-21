---
title: Error ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 7b926214d3be7f5f57783a8599acf1bb1042f956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944456"
---
# <a name="error-statement"></a>Error ステートメント
エラーの発生をシミュレートします。  
  
## <a name="syntax"></a>構文  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>指定項目  
 `errornumber`  
 必須。 任意の有効なエラー番号を指定できます。  
  
## <a name="remarks"></a>Remarks  
 ステートメント`Error`は、旧バージョンとの互換性のためにサポートされています。 新しいコードでは、特にオブジェクトを作成する`Err`ときに`Raise` 、オブジェクトのメソッドを使用して実行時エラーを生成します。  
  
 が`errornumber`定義されて`Error`いる場合、ステートメントは、 `Err`オブジェクトのプロパティに次の既定値が割り当てられた後にエラーハンドラーを呼び出します。  
  
|プロパティ|値|  
|--------------|-----------|  
|`Number`|ステートメントの`Error`引数として指定された値。 任意の有効なエラー番号を指定できます。|  
|`Source`|現在の Visual Basic プロジェクトの名前。|  
|`Description`|この文字列が存在する場合は、指定`Error` `Number`したの関数の戻り値に対応する文字列式。 文字列が存在しない場合、 `Description`には長さ0の文字列 ("") が含まれます。|  
|`HelpFile`|適切な Visual Basic ヘルプファイルの完全修飾ドライブ、パス、およびファイル名。|  
|`HelpContext`|`Number`プロパティに対応するエラーのヘルプファイルコンテキスト ID (適切な Visual Basic)。|  
|`LastDLLError`|回.|  
  
 エラーハンドラーが存在しない場合、または何も有効になっていない場合は、 `Err`エラーメッセージが作成され、オブジェクトのプロパティから表示されます。  
  
> [!NOTE]
> Visual Basic ホストアプリケーションによっては、オブジェクトを作成できない場合があります。 クラスとオブジェクトを作成できるかどうかを判断するには、ホストアプリケーションのドキュメントを参照してください。  
  
## <a name="example"></a>例  
 この例では`Error` 、ステートメントを使用して、エラー番号11を生成します。  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [Microsoft. Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **組み立て**Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume ステートメント](../../../visual-basic/language-reference/statements/resume-statement.md)
- [エラー メッセージ](../../../visual-basic/language-reference/error-messages/index.md)
