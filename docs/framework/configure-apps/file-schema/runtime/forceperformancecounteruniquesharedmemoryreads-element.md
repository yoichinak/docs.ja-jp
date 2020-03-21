---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154141"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<>要素を読み込みます。
PerfCounter.dll が、.NET Framework バージョン 1.1 のアプリケーションの CategoryOptions レジストリ設定を使用してするかどうかを指定して、カテゴリ別の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを決定します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>を読み込む**  
  
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
|`enabled`|必須の属性です。<br /><br /> PerfCounter.dll が CategoryOptions レジストリ設定を使用して、カテゴリ固有の共有メモリまたはグローバル メモリからパフォーマンス カウンタ データを読み込むかどうかを指定するかどうかを示します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|Value|説明|  
|-----------|-----------------|  
|`false`|PerfCounter.dll は、カテゴリ オプションレジストリ設定を使用しませんこれは既定です。|  
|`true`|PerfCounter.dll は、カテゴリ オプションのレジストリ設定を使用します。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  
 NET Framework 4 より前のバージョンの .NET Framework では、読み込まれた PerfCounter.dll のバージョンは、プロセスに読み込まれたランタイムに対応していました。 コンピューターに .NET Framework バージョン 1.1 と .NET Framework 2.0 の両方がインストールされている場合、.NET Framework 1.1 アプリケーションは .NET Framework 1.1 バージョンの PerfCounter.dll を読み込みます。 NET Framework 4 以降、最新のインストールバージョンの PerfCounter.dll が読み込まれます。 つまり、.NET Framework 4 がコンピュータにインストールされている場合、.NET Framework 1.1 アプリケーションは.NET Framework 4 バージョンの PerfCounter.dll を読み込みます。  
  
 パフォーマンス カウンターを使用する場合、.NET Framework 4 以降、PerfCounter.dll は、カテゴリ固有の共有メモリまたはグローバル共有メモリから読み取る必要があるかどうかを判断する各プロバイダーの CategoryOptions レジストリ エントリを確認します。 .NET Framework 1.1 PerfCounter.dll は、カテゴリ固有の共有メモリを認識していないため、レジストリ エントリを読み取りません。常にグローバル共有メモリから読み取ります。  
  
 下位互換性を維持するために、.NET Framework 1.1 アプリケーションで実行している場合、.NET Framework 4 PerfCounter.dll はカテゴリ オプションのレジストリ エントリをチェックしません。 単に.NET Framework 1.1 PerfCounter.dll と同じように、グローバル共有メモリを使用します。 ただし、.NET Framework 4 PerfCounter.dll に対して、要素を有効に`<forcePerformanceCounterUniqueSharedMemoryReads>`することでレジストリ設定を確認するように指示できます。  
  
> [!NOTE]
> 要素を`<forcePerformanceCounterUniqueSharedMemoryReads>`有効にしても、カテゴリ固有の共有メモリが使用されるとは保証されません。 設定を有効`true`にした場合にのみ、PerfCounter.dll がカテゴリ オプションレジストリ設定を参照します。 カテゴリ オプションの既定の設定では、カテゴリ固有の共有メモリを使用します。ただし、グローバル共有メモリを使用することを示すように CategoryOptions を変更できます。  
  
 カテゴリオプション設定を含むレジストリ キーは、カテゴリ名\\\>\パフォーマンスHKEY_LOCAL_MACHINE\システム\現在のコントロール セット\サービス<です。 既定では、カテゴリ オプションは 3 に設定され、カテゴリ固有の共有メモリを使用するように PerfCounter.dll に指示します。 カテゴリ オプションが 0 に設定されている場合、PerfCounter.dll はグローバル共有メモリを使用します。 インスタンスデータは、作成されるインスタンスの名前が再利用されるインスタンスと同じ場合にのみ再利用されます。 すべてのバージョンは、カテゴリに書き込むことができるでしょう。 CategoryOptions を 1 に設定すると、グローバル共有メモリが使用されますが、カテゴリ名が再利用されるカテゴリと同じ長さであればインスタンス データを再利用できます。  
  
 設定 0 と 1 は、メモリ リークやパフォーマンス カウンタ メモリの不足につながる可能性があります。  
  
## <a name="example"></a>例  
 次の例では、PerfCounter.dll がカテゴリ固有の共有メモリを使用するかどうかを判断するために CategoryOptions レジストリ エントリを参照するように指定する方法を示します。  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
