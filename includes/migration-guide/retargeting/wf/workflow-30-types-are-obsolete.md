---
ms.openlocfilehash: 70acbb571921c5f72ecaa26b26136a77532ad220
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234735"
---
### <a name="workflow-30-types-are-obsolete"></a>WorkFlow 3.0 タイプは廃止されました

|   |   |
|---|---|
|説明|Windows Workflow Foundation (WWF) 3.0 API (System.Workflow 名前空間からのもの) は廃止されました。|
|提案される解決策|新しい WWF 4.0 API (System.Activities) を代わりに使用する必要があります。 新しい API の使用例は[ここ](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)にあり、詳しいガイダンスは[ここ](https://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx)にあります。 または、WWF 3.0 API はまだサポートされているので、使用でき、ビルド時の警告は、警告を抑制することによって、または以前のコンパイラを使用することによって回避できます。|
|スコープ|Major|
|バージョン|4.5|
|型|再ターゲット中|
