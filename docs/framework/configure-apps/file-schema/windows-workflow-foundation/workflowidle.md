---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1d8ddaf5d69d87ff6112b5cbb285f0ccfda724e2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397534"
---
# <a name="workflowidle"></a>\<workflowIdle >
アイドル状態のワークフロー インスタンスのアンロードおよび永続化のタイミングを制御するサービス動作。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<system.ServiceModel >** ](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<動作 >** ](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<動作 >** ](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowIdle >**  
  
## <a name="syntax"></a>構文  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|timeToPersist|ワークフローがアイドル状態になってから永続化されるまでの期間を指定する Timespan 値。 既定値は TimeSpan です。<br /><br /> 継続時間は、ワークフロー インスタンスがアイドル状態になった時点から開始します。 この属性は、インスタンスを可能な限りメモリに保持しながら、ワークフローインスタンスをより積極的に永続化する場合に便利です。 この属性は、値が**timeToUnload**属性より小さい場合にのみ有効です。 それより大きい場合は無視されます。 **TimeToUnload**属性によって指定された値の前にこの属性が経過した場合、ワークフローがアンロードされる前に永続化を完了する必要があります。 これは、ワークフローを永続化するまでアンロード操作に遅延が生じる場合があることを意味します。 永続化レイヤーは一時的なエラーの再試行処理は行いますが、回復不可能なエラーに対しては例外をスローするだけです。 したがって、永続化中にスローされる例外は致命的な例外として処理され、ワークフロー インスタンスが中止されます。|  
|timeToUnload|ワークフローがアイドル状態からアンロードされるまでの継続時間を指定する Timespan 値。 既定値は 1 分です。<br /><br /> ワークフローをアンロードすることは、同時に、永続化することも意味します。 この属性が0に設定されている場合は、ワークフローがアイドル状態になった直後にワークフローインスタンスが永続化され、アンロードされます。 この属性を TimeSpan に設定すると、アンロード操作が実質的に無効になります。 アイドル状態になったワークフロー インスタンスはアンロードされません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<servicebehaviors の\<動作 > >](behavior-of-servicebehaviors-of-workflow.md)|動作の要素を指定します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
