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
ms.openlocfilehash: 8ac7cee2f9959bc75df165d00d3a0a67e1dd9af0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837534"
---
# <a name="error-statement"></a>Error ステートメント
エラーの発生をシミュレートします。  
  
## <a name="syntax"></a>構文  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>指定項目  
 `errornumber`  
 必須。 有効なエラー番号を指定できます。  
  
## <a name="remarks"></a>Remarks  
 `Error`ステートメントは、旧バージョンとの互換性をサポートします。 オブジェクトを作成するときに特に新しいコードを使用して、`Err`オブジェクトの`Raise`実行時エラーを生成します。  
  
 場合`errornumber`が定義されている、`Error`ステートメントのプロパティの後のエラー ハンドラーの呼び出し、`Err`オブジェクトには、次の既定値が割り当てられます。  
  
|プロパティ|[値]|  
|--------------|-----------|  
|`Number`|引数として指定された値`Error`ステートメント。 有効なエラー番号を指定できます。|  
|`Source`|現在の Visual Basic プロジェクトの名前です。|  
|`Description`|文字列式の戻り値に対応する、 `Error` 、指定された関数`Number`、この文字列が存在する場合。 文字列が存在しない場合`Description`長さ 0 の文字列が含まれています ("")。|  
|`HelpFile`|完全修飾のドライブ、パス、および適切な Visual Basic ヘルプ ファイルの名前。|  
|`HelpContext`|対応するエラーのコンテキスト ID を適切な Visual Basic ヘルプ ファイル、`Number`プロパティ。|  
|`LastDLLError`|0 を返します。|  
  
 エラー ハンドラーが存在しないか、有効でない場合、エラー メッセージが作成されから表示される場合、`Err`オブジェクトのプロパティ。  
  
> [!NOTE]
>  Visual Basic のホスト アプリケーションによっては、オブジェクトを作成できません。 クラスとオブジェクトのどちらを作成できるかどうかを判断する、ホスト アプリケーションのマニュアルを参照してください。  
  
## <a name="example"></a>例  
 この例では、 `Error` 11 のエラー番号を生成するステートメント。  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>必要条件  
 **名前空間:**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **アセンブリ:** Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume ステートメント](../../../visual-basic/language-reference/statements/resume-statement.md)
- [エラー メッセージ](../../../visual-basic/language-reference/error-messages/index.md)
