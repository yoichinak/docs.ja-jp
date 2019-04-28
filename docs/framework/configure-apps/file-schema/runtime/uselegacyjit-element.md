---
title: <useLegacyJit> 要素
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a467599084f01b1a48c95c5e25fb1f869156dffa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673889"
---
# <a name="uselegacyjit-element"></a>\<useLegacyJit> 要素

共通言語ランタイムが Just-In-Time コンパイルの従来の 64 ビット JIT コンパイラを使用するかどうかを決定します。  
  
\<configuration>  
\<runtime>  
\<useLegacyJit >
  
## <a name="syntax"></a>構文  
  
```xml
<useLegacyJit enabled=0|1 />
```

要素名`useLegacyJit`小文字が区別されます。
  
## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
| 属性 | 説明                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | 必須の属性です。<br><br>ランタイムが従来の 64 ビット JIT コンパイラを使用するかどうかを指定します。 |  
  
### <a name="enabled-attribute"></a>enabled 属性  
  
| [値] | 説明                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | 共通言語ランタイムは、.NET Framework 4.6 および以降のバージョンに含まれる新しい 64 ビット JIT コンパイラを使用します。 |  
| 1     | 共通言語ランタイムは、古い 64 ビット JIT コンパイラを使用します。                                                     |  
  
### <a name="child-elements"></a>子要素

なし
  
### <a name="parent-elements"></a>親要素  
  
| 要素         | 説明                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |  
| `runtime`       | ランタイム初期化オプションに関する情報を含んでいます。                                                        |  
  
## <a name="remarks"></a>Remarks  

以降、.NET Framework 4.6 では、共通言語ランタイムを使用して新しい 64 ビット コンパイラの Just-In-Time (JIT) コンパイル既定。 場合によっては、64 ビット JIT コンパイラの以前のバージョンで JIT コンパイルされたアプリケーション コードからの動作の違いにあります。 設定して、`enabled`の属性、`<useLegacyJit>`要素`1`、新しい 64 ビット JIT コンパイラを無効にし、代わりに、従来の 64 ビット JIT コンパイラを使用して、アプリをコンパイルすることができます。  
  
> [!NOTE]
> `<useLegacyJit>`要素が 64 ビット JIT コンパイルのみに影響します。 32 ビット JIT コンパイラによるコンパイルには影響を受けません。  
  
構成ファイルの設定を使用する代わりに、その他の 2 つの方法では、従来の 64 ビット JIT コンパイラが有効にできます。  
  
- 環境変数の設定

  設定、`COMPLUS_useLegacyJit`するか、環境変数`0`(新しい 64 ビット JIT コンパイラを使用) または`1`(以前の 64 ビット JIT コンパイラを使用)。
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  環境変数が*グローバル スコープ*マシン上のすべてのアプリケーションで実行に影響を与えることを意味します。 かどうか設定をオーバーライドできますでアプリケーション構成ファイルの設定。 環境変数名は区別されません。
  
- レジストリ キーを追加します。

  追加することで、従来の 64 ビット JIT コンパイラを有効にすることができます、`REG_DWORD`いずれかの値、`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`または`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`レジストリのキー。 値の名前は`useLegacyJit`します。 値が 0 の場合は、新しいコンパイラが使用されます。 値が 1 の場合は、従来の 64 ビット JIT コンパイラが有効にします。 レジストリ値の名前は区別されません。
  
  値を追加、`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`キー、マシンで実行されているすべてのアプリに影響を与えます。 値を追加、`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`キーが現在のユーザーが実行するすべてのアプリに影響します。 マシンには、複数のユーザー アカウントを構成、現在のユーザーが実行するアプリのみに影響、値が他のユーザーのレジストリ キーを追加しない限り、します。 追加、`<useLegacyJit>`要素を構成ファイルが存在する場合、レジストリに設定をオーバーライドします。  
  
## <a name="example"></a>例  

次の構成ファイルでは、新しい 64 ビット JIT コンパイラでコンパイルを無効にし、代わりに、従来の 64 ビット JIT コンパイラを使用します。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [\<ランタイム > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [\<configuration> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
- [軽減策:新しい 64 ビット JIT コンパイラ](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
