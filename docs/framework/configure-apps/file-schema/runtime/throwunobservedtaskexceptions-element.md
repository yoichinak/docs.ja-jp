---
title: <ThrowUnobservedTaskExceptions> 要素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153816"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<要素>監視タスク例外
タスクがハンドルされない例外によって実行中のプロセスを終了するかどうかを指定します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ハンドルされないタスク例外が実行中のプロセスを終了するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|Value|説明|  
|-----------|-----------------|  
|`false`|ハンドルされないタスク例外の実行中のプロセスを終了しません。 これは既定値です。|  
|`true`|ハンドルされないタスク例外の実行中のプロセスを終了します。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
|||  
  
## <a name="remarks"></a>解説  
 に関連付けられた例外<xref:System.Threading.Tasks.Task>が観測されていない場合、操作はなく<xref:System.Threading.Tasks.Task.Wait%2A>、親はアタッチされず、<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>プロパティが読み取られておらず、タスク例外は監視されないと見なされます。  
  
 NET Framework 4 では、既定では、例外<xref:System.Threading.Tasks.Task>が発生していないがガベージ コレクションされた場合、ファイナライザーは例外をスローし、プロセスを終了します。 プロセスの終了は、ガベージ コレクションとファイナライズのタイミングによって決まります。  
  
 開発者がタスクに基づいて非同期コードを記述しやすくするために、.NET Framework 4.5 では、例外が発生していない場合に、この既定の動作が変更されます。 例外が発生しても例外が発生<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>してもイベントは発生しますが、既定ではプロセスは終了しません。 代わりに、イベント ハンドラーが例外を監視するかどうかに関係なく、イベントが発生した後に例外は無視されます。  
  
 NET Framework 4.5 では、アプリケーション構成ファイルの[\<ThrowUn観測TaskExceptions>要素](throwunobservedtaskexceptions-element.md)を使用して、例外をスローする .NET Framework 4 の動作を有効にすることができます。  
  
 例外の動作は、次のいずれかの方法で指定することもできます。  
  
- 環境変数`COMPlus_ThrowUnobservedTaskExceptions`を設定することにより(`set COMPlus_ThrowUnobservedTaskExceptions=1`)  
  
- レジストリ DWORD 値を設定することで、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft でタスク例外 =\\1 を指定します。キーを使用します。  
  
## <a name="example"></a>例  
 アプリケーション構成ファイルを使用して、タスクで例外のスローを有効にする方法を次の例に示します。  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>例  
 次の例は、監視されていない例外がタスクからスローされる方法を示しています。 コードが正しく動作するには、リリース済みプログラムとして実行する必要があります。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
