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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ed1e66c4aadab656455686a7a1e5028b035676a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252269"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions > 要素
タスクがハンドルされない例外によって実行中のプロセスを終了するかどうかを指定します。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<ランタイム >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<ThrowUnobservedTaskExceptions>**  
  
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
|`enabled`|必須の属性です。<br /><br /> 未処理のタスク例外が実行中のプロセスを終了するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|は、未処理のタスク例外の実行中のプロセスを終了しません。 既定値です。|  
|`true`|未処理のタスク例外の実行中のプロセスを終了します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
|||  
  
## <a name="remarks"></a>Remarks  
 に関連付けら<xref:System.Threading.Tasks.Task>れている例外がまだ確認されていない場合、操作がなく<xref:System.Threading.Tasks.Task.Wait%2A> 、親がアタッチ<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>されておらず、プロパティが読み取られていない場合、タスクの例外は監視されと見なされます。  
  
 .NET Framework 4 では、監視され例外が発生し<xref:System.Threading.Tasks.Task>たがガベージコレクションされた場合、ファイナライザーは例外をスローしてプロセスを終了します。 プロセスの終了は、ガベージコレクションと終了処理のタイミングによって決まります。  
  
 開発者がタスクに基づいて非同期コードを簡単に記述できるように、.NET Framework 4.5 では、監視され例外のこの既定の動作が変更されています。 監視され例外が発生し<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>てもイベントは発生しますが、既定ではプロセスは終了しません。 代わりに、イベントハンドラーが例外を監視しているかどうかに関係なく、イベントが発生した後に例外が無視されます。  
  
 .NET Framework 4.5 では、アプリケーション構成ファイルの[ \<ThrowUnobservedTaskExceptions > 要素](throwunobservedtaskexceptions-element.md)を使用して、例外をスローする .NET Framework 4 の動作を有効にすることができます。  
  
 例外の動作は、次のいずれかの方法で指定することもできます。  
  
- 環境変数`COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`) を設定する。  
  
- レジストリの DWORD 値 ThrowUnobservedTaskExceptions = 1 を HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\に設定します。NETFramework キー。  
  
## <a name="example"></a>例  
 次の例では、アプリケーション構成ファイルを使用して、タスクで例外のスローを有効にする方法を示します。  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>例  
 次の例では、タスクから監視され例外がスローされる方法を示します。 コードを正常に動作させるには、リリースされたプログラムとして実行する必要があります。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
