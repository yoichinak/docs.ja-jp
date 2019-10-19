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
ms.openlocfilehash: c7b2adfe7f6b6ff5e89598cb318a90c51595ff6f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583380"
---
# <a name="error-statement"></a>Error ステートメント
エラーの発生をシミュレートします。  
  
## <a name="syntax"></a>構文  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>指定項目  
 `errornumber`  
 必須です。 任意の有効なエラー番号を指定できます。  
  
## <a name="remarks"></a>Remarks  
 @No__t_0 ステートメントは、旧バージョンとの互換性のためにサポートされています。 新しいコードでは、特にオブジェクトを作成する場合は、`Err` オブジェクトの `Raise` メソッドを使用して、実行時エラーを生成します。  
  
 @No__t_0 が定義されている場合、`Err` オブジェクトのプロパティに次の既定値が割り当てられると、`Error` ステートメントによってエラーハンドラーが呼び出されます。  
  
|property|[値]|  
|--------------|-----------|  
|`Number`|@No__t_0 ステートメントの引数として指定された値。 任意の有効なエラー番号を指定できます。|  
|`Source`|現在の Visual Basic プロジェクトの名前。|  
|`Description`|この文字列が存在する場合は、指定された `Number` の `Error` 関数の戻り値に対応する文字列式。 文字列が存在しない場合、`Description` には長さ0の文字列 ("") が含まれます。|  
|`HelpFile`|適切な Visual Basic ヘルプファイルの完全修飾ドライブ、パス、およびファイル名。|  
|`HelpContext`|@No__t_0 プロパティに対応するエラーの Visual Basic ヘルプファイルコンテキスト ID。|  
|`LastDLLError`|回.|  
  
 エラーハンドラーが存在しない場合、または何も有効になっていない場合は、エラーメッセージが作成され、`Err` オブジェクトのプロパティから表示されます。  
  
> [!NOTE]
> Visual Basic ホストアプリケーションによっては、オブジェクトを作成できない場合があります。 クラスとオブジェクトを作成できるかどうかを判断するには、ホストアプリケーションのドキュメントを参照してください。  
  
## <a name="example"></a>例  
 この例では、`Error` ステートメントを使用して、エラー番号11を生成します。  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>［要件］  
 **名前空間:** [Microsoft. visual basic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **アセンブリ:** Visual Basic ランタイムライブラリ (Microsoft... .dll)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume ステートメント](../../../visual-basic/language-reference/statements/resume-statement.md)
- [エラー メッセージ](../../../visual-basic/language-reference/error-messages/index.md)
