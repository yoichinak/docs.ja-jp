---
ms.openlocfilehash: 5b3f9bcb56d3e34568afd8b97fb9ebe09a677f4c
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802657"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET 相互運用で IAgileObject に対して QueryInterface が呼び出されるようになる (WinRT インターフェイス)

|   |   |
|---|---|
|説明|.NET デリゲートで WinRT イベントを使用する場合、.NET Framework 4.8 以降では、Windows で IAgileObject に対して QI が呼び出されます。  .NET Framework の以前のバージョンでは、ランタイムでその QI が失敗し、イベントをサブスクライブできませんでした。<ul><li>[ x ] 後方互換</li></ul>|
|提案される解決策|IAgileObject に対して QI を有効にすると実行が中断される場合は、次の構成を設定し、このコードを無効にすることができます。 <h4>方法 1:環境変数</h4> 環境変数を COMPLUS_DisableCCWSupportIAgileObject=1 に設定します。この方法は、この環境変数を継承するすべての環境に影響します。 この場合、コンソール セッションが 1 つのみになる可能性があります。あるいは、環境変数をグローバルに設定した場合、コンピューター全体に影響する可能性があります。環境変数の名前では大文字と小文字は区別されません。 <h4>方法 2:レジストリ</h4> レジストリ エディター (regedit.exe) を使用して、サブキーの HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework または HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFramework を見つけます。その後、次のように追加します。値の名前:DisableCCWSupportIAgileObject 種類:DWORD (32 ビット) 値 (REG_WORD ともいう) 値:1。Windows REG.EXE ツールを使用して、コマンド ラインまたはスクリプト環境から、この値を追加することができます。 次に例を示します。<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>ここでは、<code>HKLM</code> が <code>HKEY_LOCAL_MACHINE</code> の代わりに使用されています。 <code>reg add /?</code> を使用すると、この構文のヘルプが表示されます。レジストリ値の名前では大文字と小文字は区別されません。|
|スコープ|エッジ|
|Version|4.8|
|型|ランタイム|

