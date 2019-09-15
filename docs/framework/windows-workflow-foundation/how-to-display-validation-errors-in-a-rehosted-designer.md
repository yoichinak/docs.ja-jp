---
title: '方法: 再ホストされたデザイナーの検証エラーを表示する'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: 608868882f4bec23c03f0ec78f65673e76056030
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989664"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>方法: 再ホストされたデザイナーの検証エラーを表示する
このトピックでは、再ホストされた [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]で検証エラーを取得および発行する方法について説明します。 再ホストされたデザイナー内のワークフローが有効であることを確認するために手順を示します。  
  
 このタスクは 2 つの部分で構成されています。 最初に、<xref:System.Activities.Presentation.Validation.IValidationErrorService> を実装します。  このインターフェイスには、1 つの重要なメソッド <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> を実装します。このメソッドは、エラーに関する情報を含む <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> オブジェクトの一覧をデバッグ ログに渡します。  このインターフェイスを実装した後に、その実装のインスタンスを編集コンテキストに発行して、エラー情報を取得します。  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>IValidationErrorService インターフェイスの実装  
  
1. 以下に、検証エラーをデバッグ ログに書き込む単純な実装を表すコード例を示します。  
  
    ```csharp  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a>編集コンテキストへの発行  
  
1. 以下に、編集コンテキストに発行するコードを示します。  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
