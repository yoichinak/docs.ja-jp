---
ms.openlocfilehash: 2cd107dc92fd0fae89717c38840ce7ea44f3ac9a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233999"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>WPF のマスター/詳細シナリオで ADO データを表示するときに主キーが変更される

|   |   |
|---|---|
|説明|<code>Order</code> 型の項目の ADO コレクションと、それを主キー &quot;OrderID&quot; によって <code>Detail</code> 型の項目のコレクションに関連付ける &quot;OrderDetails&quot; という関係があるとします。 WPF アプリでは、特定の順序の詳細にリスト コントロールをバインドできます。<pre><code class="lang-xml">&lt;ListBox ItemsSource=&quot;{Binding Path=OrderDetails}&quot; &gt;&#13;&#10;</code></pre>ここで、DataContext は <code>Order</code> です。 WPF は、<code>OrderDetails</code> プロパティの値 (<code>OrderID</code> がマスター項目の <code>OrderID</code> と一致するすべての <code>Detail</code> 項目のコレクション D) を取得します。マスター項目の主キー <code>OrderID</code> を変更すると、動作変更が発生します。 ADO は、Details コレクション内の影響を受ける各レコード (つまり、コレクション D にコピーされたレコード) の <code>OrderID</code> を自動的に変更します。  では、D はどうなるのでしょうか?<ul><li>以前の動作: コレクション D はクリアされます。   マスター項目では、プロパティ  <em>の変更通知が</em>発生しません<code>OrderDetails</code>。  ListBox は、空になったコレクション D を引き続き使用します。</li><li>新しい動作:コレクション D は変更されません。   その各項目で、<code>OrderID</code> プロパティの変更通知が発生します。  ListBox はコレクション D を引き続き使用し、新しい <code>OrderID</code> に関する詳細を表示します。</li></ul>WPF は、別の方法 (<code>followParent</code> 引数を <code>true</code> に設定して ADO メソッド <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> を呼び出す) でコレクション D を作成することにより、新しい動作を実装します。|
|提案される解決策|アプリは、次の AppContext スイッチを使用して新しい動作を取得します。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;&#13;&#10;</code></pre>スイッチの既定値は、.NET 4.7.1 以下を対象とするアプリでは <code>true</code> に設定され (古い動作)、.NET 4.7.2 以上を対象とするアプリでは <code>false</code> に設定されます (新しい動作)。|
|スコープ|マイナー|
|Version|4.7.2|
|型|再ターゲット中|
