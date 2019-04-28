---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d4a205f643c844b2fe77d3aa5211b4bc1f322fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674253"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads > 要素
PerfCounter.dll が、.NET Framework バージョン 1.1 のアプリケーションの CategoryOptions レジストリ設定を使用してするかどうかを指定して、カテゴリ別の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを決定します。  
  
 \<configuration>  
\<runtime>  
\<forcePerformanceCounterUniqueSharedMemoryReads>  
  
## <a name="syntax"></a>構文  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> どちらがカテゴリ別の共有メモリとグローバル メモリからパフォーマンス カウンター データを読み込むかどうかを判断する CategoryOptions レジストリ設定を使用するかどうかを示します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|どちらを使用しません、CategoryOptions レジストリ設定ではこれが既定値。|  
|`true`|どちらでは、CategoryOptions レジストリ設定を使用します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 前に .NET Framework のバージョンでは、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、読み込まれているどちらのバージョンは、プロセスに読み込まれたランタイムに対応します。 かどうか、コンピューターが両方の .NET Framework version 1.1 と[!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)]、インストールされている .NET Framework 1.1 アプリケーションはどちらの .NET Framework 1.1 バージョンを読み込まれます。 以降では、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]どちらのインストールされている最新のバージョンが読み込まれます。 つまり、.NET Framework 1.1 アプリケーションが読み込むこと、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]バージョンどちらの場合、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]がコンピューターにインストールされています。  
  
 以降では、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]、パフォーマンス カウンターを使用するときにどちらがカテゴリ別の共有メモリまたはグローバル共有メモリから読み取る必要があります、かどうかを確認するには、各プロバイダーの CategoryOptions レジストリ エントリを確認します。 カテゴリに固有の共有メモリの対応でないため、.NET Framework 1.1 のどちらがレジストリのエントリを読み取れませんグローバル共有メモリから常に読み込みます。  
  
 旧バージョンとの互換性のため、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] .NET Framework 1.1 アプリケーションの実行時にどちらが CategoryOptions レジストリ エントリを確認できません。 単に、.NET Framework 1.1 のどちらの場合と同様のグローバル共有メモリを使用します。 ただし、指示すること、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]どちらを有効にすると、レジストリ設定を確認する、`<forcePerformanceCounterUniqueSharedMemoryReads>`要素。  
  
> [!NOTE]
>  有効にすると、`<forcePerformanceCounterUniqueSharedMemoryReads>`要素がカテゴリ別の共有メモリが使用されることを保証していません。 設定を有効になっている`true`CategoryOptions レジストリ設定を参照するどちらでのみ発生します。 CategoryOptions の既定の設定は、カテゴリ固有の共有メモリを使用することです。ただし、グローバル共有メモリを使用することを示す CategoryOptions を変更できます。  
  
 CategoryOptions 設定を格納するレジストリ キーは hkey_local_machine \system\currentcontrolset\services\\< categoryName\>\Performance します。 既定では、CategoryOptions は設定を 3 にどちら カテゴリ固有の共有メモリを使用します。 CategoryOptions が 0 に設定されている場合、どちらはグローバル共有メモリを使用します。 作成中のインスタンスの名前は再利用されるインスタンスと同じ場合にのみ、インスタンス データを再利用されます。 すべてのバージョンは、カテゴリに書き込みを可能になります。 CategoryOptions が 1 に設定されている場合は、グローバル共有メモリが使用されますが、カテゴリ名が再利用されるカテゴリと同じ長さである場合は、インスタンス データを再利用されることができます。  
  
 0 と 1 の設定は、メモリ リークおよびパフォーマンス カウンターのメモリの不足につながります。  
  
## <a name="example"></a>例  
 次の例では、どちらがカテゴリ別の共有メモリを使用するかどうかを判断する CategoryOptions レジストリ エントリを参照する必要がありますを指定する方法を示します。  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
