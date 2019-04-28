---
title: 拡張可能オブジェクト
ms.date: 03/30/2017
helpviewer_keywords:
- extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
ms.openlocfilehash: 1af44f2394bbf27f9219831612b4e73d7a1759e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857884"
---
# <a name="extensible-objects"></a>拡張可能オブジェクト

拡張可能オブジェクト パターンは、既存のランタイム クラスに新しい機能を付加して拡張したり、オブジェクトに新しい状態を追加するために使用します。 このようなオブジェクトを実際に拡張することにより、処理の段階に応じて、共通の拡張可能オブジェクトに定義された共有の状態や機能にアクセスすることができます。

## <a name="the-iextensibleobjectt-pattern"></a>IExtensibleObject\<T > パターン

拡張可能オブジェクト パターンには、<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601>、および <xref:System.ServiceModel.IExtensionCollection%601> の 3 つのインターフェイスがあります。

<xref:System.ServiceModel.IExtensibleObject%601> インターフェイスを実装することにより、<xref:System.ServiceModel.IExtension%601> オブジェクトの機能をカスタマイズできます。

拡張可能オブジェクトを使用すると、<xref:System.ServiceModel.IExtension%601> オブジェクトの動的な集約が可能になります。 <xref:System.ServiceModel.IExtension%601> オブジェクトには、次のインターフェイスが実装されています。

```csharp
public interface IExtension<T>
where T : IExtensibleObject<T>
{
    void Attach(T owner);
    void Detach(T owner);
}
```

この型制約は、<xref:System.ServiceModel.IExtensibleObject%601> であるクラスに対してしか拡張を定義できないことを保証します。 <xref:System.ServiceModel.IExtension%601.Attach%2A> と <xref:System.ServiceModel.IExtension%601.Detach%2A> は、集約や集約解除に関する通知を提供します。

所有者が追加や削除を行う際の制限を組み込むことも可能です。 たとえば、削除は全面的に禁止する、所有者や拡張がある状態であれば拡張の追加や削除を禁止する、同時に複数の所有者に追加することを禁止する、1 つ削除したら 1 つだけ追加を許可する、などの制約を指定することができます。

<xref:System.ServiceModel.IExtension%601> を実装しても、他の標準のマネージド インターフェイスとやりとりできるとは限りません。 特に、所有者オブジェクトの <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> メソッドは、自分自身の拡張を解除しないのが普通です。

拡張機能は、コレクションに追加されたときに<xref:System.ServiceModel.IExtension%601.Attach%2A>コレクションに入る前に呼び出されます。 拡張機能は、コレクションから削除されたときに<xref:System.ServiceModel.IExtension%601.Detach%2A>が削除された後に呼び出されます。 (適切な同期を想定) 手段でのみ、その中にコレクション内で見つかった拡張機能をカウントできますこの間隔は<xref:System.ServiceModel.IExtension%601.Attach%2A>と<xref:System.ServiceModel.IExtension%601.Detach%2A>します。

<xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> や <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> に渡すオブジェクトは、<xref:System.ServiceModel.IExtension%601> である必要はなく、任意のオブジェクトを渡すことができますが、返される拡張は <xref:System.ServiceModel.IExtension%601> です。

コレクション内の拡張機能がない場合、 <xref:System.ServiceModel.IExtension%601>、<xref:System.ServiceModel.IExtensionCollection%601.Find%2A>は null を返しますと<xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A>空のコレクションを返します。 複数の拡張機能を実装して場合<xref:System.ServiceModel.IExtension%601>、<xref:System.ServiceModel.IExtensionCollection%601.Find%2A>うち 1 つを返します。 <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> から返される値はスナップショットです。

主な使い方として、次の 2 つのシナリオが考えられます。 1 つ目のシナリオでは、型ベースのディクショナリとして <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> プロパティを使用し、オブジェクトに状態を追加します。これは、別のコンポーネントが型に基づいて検索できます。

2 つ目のシナリオでは、<xref:System.ServiceModel.IExtension%601.Attach%2A> プロパティおよび <xref:System.ServiceModel.IExtension%601.Detach%2A> プロパティを使用し、イベントへの登録や、状態の遷移の監視など、カスタムの動作にオブジェクトを参加させます。

<xref:System.ServiceModel.IExtensionCollection%601> インターフェイスは、型を基準にした <xref:System.ServiceModel.IExtension%601> の取得を可能にする <xref:System.ServiceModel.IExtension%601> オブジェクトのコレクションです。 <xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType> は、指定された型の <xref:System.ServiceModel.IExtension%601> オブジェクトのうち、最も新しく追加されたものを返します。

### <a name="extensible-objects-in-windows-communication-foundation"></a>Windows Communication Foundation の拡張可能オブジェクト

Windows Communication Foundation (WCF) の 4 つの拡張可能なオブジェクトがあります。

- <xref:System.ServiceModel.ServiceHostBase> : サービス ホストの基本クラスです。  <xref:System.ServiceModel.ServiceHostBase> 自身の動作を拡張するほか、各サービスの状態を保存しておくための拡張が可能です。

- <xref:System.ServiceModel.InstanceContext> : サービスのランタイムを使用して、サービスの型のインスタンスと接続するためのクラスです。  このクラスは、インスタンスに関する情報のほか、<xref:System.ServiceModel.InstanceContext> に含まれる <xref:System.ServiceModel.ServiceHostBase> への参照を保持します。 <xref:System.ServiceModel.InstanceContext> 自身の動作を拡張するほか、各サービスの状態を保存しておくための拡張が可能です。

- <xref:System.ServiceModel.OperationContext> : 操作ごとにランタイムが収集した操作情報を表すクラスです。  具体的には、受け取ったメッセージのヘッダーやプロパティ、受け取ったセキュリティ ID などの情報があります。  <xref:System.ServiceModel.OperationContext> 自身の動作を拡張するほか、各操作の状態を保存しておくための拡張が可能です。

- <xref:System.ServiceModel.IContextChannel> – このインターフェイスは、チャネルと、WCF ランタイムによって作成されたプロキシの各状態の検査できます。  <xref:System.ServiceModel.IClientChannel> 自身の動作を拡張するほか、各チャネルの状態を保存しておくための拡張が可能です。

<xref:System.ServiceModel.InstanceContext> オブジェクトの状態を追跡するという、簡単な拡張の使い方を例示したコードを次に示します。

[!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.IExtensibleObject%601>
- <xref:System.ServiceModel.IExtension%601>
- <xref:System.ServiceModel.IExtensionCollection%601>
