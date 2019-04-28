---
title: データ連結に関連するインターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], data-binding interfaces
- INotifyPropertyChanged interface
- IBindingListView interface
- IList interface [Windows Forms], Windows Forms data binding
- IBindingList interface [Windows Forms], Windows Forms data binding
- interfaces [Windows Forms], Windows Forms data binding
- IEditableObject interface [Windows Forms], Windows Forms data binding
- data binding [Windows Forms], interfaces
- IDataErrorInfo interface [Windows Forms], Windows Forms data binding
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
ms.openlocfilehash: ffda85b2704212ea5323117447e0cfe17ffb33db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801778"
---
# <a name="interfaces-related-to-data-binding"></a>データ連結に関連するインターフェイス

[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] では、アプリケーションのバインドのニーズや使用するデータに合わせてさまざまなデータ構造を作成できます。 Windows フォームでデータを提供または使用するための独自のクラスを作成することもできます。 これらのオブジェクトは、基本的なデータ バインディングから、デザイン時サポートの提供、エラー チェック、変更通知、データ自体に加えられた変更の構造化されたロールバックのサポートに至るまで、さまざまなレベルの機能を提供することができ、複雑さに対応できます。

## <a name="consumers-of-data-binding-interfaces"></a>データ バインディング インターフェイスのコンシューマー

以下のセクションでは、インターフェイス オブジェクトの 2 つのグループについて説明します。 1 つ目のグループでは、データ ソース作成者がデータ ソースに実装するインターフェイスを示します。 これらのインターフェイスは、データ ソース コンシューマーが使用するように設計されています。ほとんどの場合、データ ソース コンシューマーは、Windows フォーム コントロールまたはコンポーネントです。 2 つ目のグループでは、コンポーネント作成者向けに設計されたインターフェイスを示します。 コンポーネント作成者は、Windows フォーム データ バインディング エンジンが使用する、データ バインディングをサポートするコンポーネントを作成するときにこれらのインターフェイスを使用します。 フォームに関連付けられたクラス内でこれらのインターフェイスを実装することで、データ バインディングを実現できます。各ケースは、データの操作を可能にするインターフェイスを実装するクラスを示しています。 Visual Studio アプリケーションの迅速な開発 (RAD) データ デザイン エクスペリエンス ツールでは、この機能のこと既に活用します。

### <a name="interfaces-for-implementation-by-data-source-authors"></a>データ ソース作成者が実装するインターフェイス

以下のインターフェイスは、Windows フォーム コントロールで使用するように設計されています。

- <xref:System.Collections.IList> インターフェイス

  実装するクラス、<xref:System.Collections.IList>インターフェイス可能性があります、 <xref:System.Array>、 <xref:System.Collections.ArrayList>、または<xref:System.Collections.CollectionBase>します。 これらの種類の項目のインデックス付きリストは、<xref:System.Object>します。 インデックスの最初の項目によって型が決定されるため、これらのリストには同種の型が含まれている必要があります。 <xref:System.Collections.IList> 実行時にのみバインドできるようになります。

  > [!NOTE]
  >  Windows フォームでビジネス オブジェクトのバインドの一覧を作成する場合は、使用を検討する必要があります、<xref:System.ComponentModel.BindingList%601>します。 <xref:System.ComponentModel.BindingList%601>双方向 Windows フォーム データ バインディングに必要な主要インターフェイスを実装する拡張可能なクラスです。

- <xref:System.ComponentModel.IBindingList> インターフェイス

  実装するクラス、<xref:System.ComponentModel.IBindingList>インターフェイスには、データ バインディング機能の非常に高いレベルが用意されています。 この実装では、基本的な並べ替え機能と変更通知を提供します。変更通知では、リスト項目が変更されたとき (たとえば、顧客リストの 3 番目の項目の Address フィールドが変更されたとき) と、リスト自体が変更されたとき (たとえば、リスト内の項目の数が増減したとき) のどちらの場合も変更が通知されます。 複数のコントロールを同じデータにバインドする予定であり、いずれかのコントロールで行われたデータ変更をバインドされた他のコントロールに反映させる必要がある場合に、変更通知が重要になります。

  > [!NOTE]
  > 変更通知が有効になって、<xref:System.ComponentModel.IBindingList>によってインターフェイスを<xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A>プロパティがときに、 `true`、発生させる、<xref:System.ComponentModel.IBindingList.ListChanged>イベント、変更一覧または一覧内の項目を示す変更します。

  変更の種類は、<xref:System.ComponentModel.ListChangedType>のプロパティ、<xref:System.ComponentModel.ListChangedEventArgs>パラメーター。 したがって、データ モデルが更新されるたびに、依存するビュー (同じデータ ソースにバインドされた他のコントロールなど) も更新されます。 ただし、リスト内に含まれるオブジェクトがリストにリストを発生させることができるように変更するときに通知する必要が、<xref:System.ComponentModel.IBindingList.ListChanged>イベント。

  > [!NOTE]
  > <xref:System.ComponentModel.BindingList%601>の汎用実装を提供します、<xref:System.ComponentModel.IBindingList>インターフェイス。

- <xref:System.ComponentModel.IBindingListView> インターフェイス

  実装するクラス、<xref:System.ComponentModel.IBindingListView>インターフェイスの実装のすべての機能を提供する<xref:System.ComponentModel.IBindingList>に加えて、としてフィルター処理および高度な並べ替え機能します。 この実装では、文字列ベースのフィルター処理と、プロパティ記述子と方向のペアによる複数列の並べ替え機能を提供します。

- <xref:System.ComponentModel.IEditableObject> インターフェイス

  実装するクラス、<xref:System.ComponentModel.IEditableObject>インターフェイスにより、そのオブジェクトへの変更を永続的なものとを制御するオブジェクト。 この実装により、 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、 <xref:System.ComponentModel.IEditableObject.EndEdit%2A>、および<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>メソッドで、オブジェクトに加えられた変更をロールバックすることを有効にします。 機能の簡単な説明を次に、 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、 <xref:System.ComponentModel.IEditableObject.EndEdit%2A>、および<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>メソッドと組み合わせて、データに加えられた変更のロールバックを実現するために相互しくみ。

  - <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>メソッドがオブジェクトでの編集の開始を通知します。 このインターフェイスを実装するオブジェクトが後に、更新プログラムを保存する必要があります、<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>メソッドの呼び出し、更新プログラムを破棄できるように場合、<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>メソッドが呼び出されます。 データ バインディング Windows フォームで呼び出すことができます<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>複数回、1 つのスコープ内で編集トランザクション (たとえば、 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、 <xref:System.ComponentModel.IEditableObject.EndEdit%2A>)。 実装<xref:System.ComponentModel.IEditableObject>かどうかを追跡する必要があります<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>が既に呼び出され、後続の呼び出しを無視<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>します。 このメソッドは、複数回呼び出すことが、ため後続の呼び出しが非破壊的な; ことが重要です。後続<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>呼び出しが行われたまたは保存されたデータを変更する更新プログラムを破棄できません。 最初の<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>呼び出します。

  - <xref:System.ComponentModel.IEditableObject.EndEdit%2A>メソッドは、以降のすべての変更をプッシュ<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>を基になるオブジェクトにオブジェクトが現在編集モードである場合に呼び出されました。

  - <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>メソッドは、オブジェクトに加えられた変更を破棄します。

  方法の詳細については<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、 <xref:System.ComponentModel.IEditableObject.EndEdit%2A>、および<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>メソッドの動作を参照してください[データをデータベースに保存](/visualstudio/data-tools/save-data-back-to-the-database)します。

  データ機能のこのトランザクションの概念を使って、<xref:System.Windows.Forms.DataGridView>コントロール。

- <xref:System.ComponentModel.ICancelAddNew> インターフェイス

  実装するクラス、<xref:System.ComponentModel.ICancelAddNew>インターフェイスは通常、実装、<xref:System.ComponentModel.IBindingList>インターフェイスし、のデータ ソースへの追加をロールバックすることができます、<xref:System.ComponentModel.IBindingList.AddNew%2A>メソッド。 場合は、データ ソースの実装、<xref:System.ComponentModel.IBindingList>インターフェイスも必要、実装、<xref:System.ComponentModel.ICancelAddNew>インターフェイス。

- <xref:System.ComponentModel.IDataErrorInfo> インターフェイス

  実装するクラス、<xref:System.ComponentModel.IDataErrorInfo>インターフェイスにより、バインドされたコントロールにカスタム エラー情報を提供するオブジェクト。

  - <xref:System.ComponentModel.IDataErrorInfo.Error%2A>プロパティは、一般的なエラー メッセージ テキストを返します (たとえば、「エラーが発生しました」)。

  - <xref:System.ComponentModel.IDataErrorInfo.Item%2A>プロパティは、列から特定のエラー メッセージ文字列を返します (たとえば、"の値、`State`列は無効です")。

- <xref:System.Collections.IEnumerable> インターフェイス

  実装するクラス、<xref:System.Collections.IEnumerable>によってインターフェイスが使用される通常[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]します。 このインターフェイスのサポートを Windows フォームはのみ、<xref:System.Windows.Forms.BindingSource>コンポーネント。

  > [!NOTE]
  > <xref:System.Windows.Forms.BindingSource>コンポーネントがすべてコピー<xref:System.Collections.IEnumerable>バインディングのための独立したリストにアイテムをします。

- <xref:System.ComponentModel.ITypedList> インターフェイス

  実装するコレクション クラス、<xref:System.ComponentModel.ITypedList>インターフェイスには、順序と、バインドされたコントロールに公開されるプロパティのセットを制御する機能が用意されています。

  > [!NOTE]
  > 実装する場合、<xref:System.ComponentModel.ITypedList.GetItemProperties%2A>メソッド、および<xref:System.ComponentModel.PropertyDescriptor>配列が null でないと、配列の最後のエントリは項目の一覧をもう 1 つであるリスト プロパティを説明するプロパティ記述子になります。

- <xref:System.ComponentModel.ICustomTypeDescriptor> インターフェイス

  実装するクラス、<xref:System.ComponentModel.ICustomTypeDescriptor>インターフェイス自体に関する動的な情報を提供します。 このインターフェイスはのような<xref:System.ComponentModel.ITypedList>がリストではなく、オブジェクトに使用されます。 このインターフェイスを使って<xref:System.Data.DataRowView>基になる行のスキーマをプロジェクトにします。 単純な実装<xref:System.ComponentModel.ICustomTypeDescriptor>によって提供される、<xref:System.ComponentModel.CustomTypeDescriptor>クラス。

  > [!NOTE]
  > デザイン時のバインドをサポートする型を実装<xref:System.ComponentModel.ICustomTypeDescriptor>、型を実装する必要がありますも<xref:System.ComponentModel.IComponent>フォーム上のインスタンスとして存在します。

- <xref:System.ComponentModel.IListSource> インターフェイス

  実装するクラス、<xref:System.ComponentModel.IListSource>インターフェイスが非リスト オブジェクトでリストベース バインディングを使用します。 <xref:System.ComponentModel.IListSource.GetList%2A>メソッドの<xref:System.ComponentModel.IListSource>から継承されていないオブジェクトからバインド可能なリストを返すために使用<xref:System.Collections.IList>します。 <xref:System.ComponentModel.IListSource> 使って、<xref:System.Data.DataSet>クラス。

- <xref:System.ComponentModel.IRaiseItemChangedEvents> インターフェイス

  実装するクラス、<xref:System.ComponentModel.IRaiseItemChangedEvents>インターフェイスも実装するバインド可能なリストは、<xref:System.ComponentModel.IBindingList>インターフェイス。 このインターフェイスの使用を示すかどうか、型が発生します<xref:System.ComponentModel.IBindingList.ListChanged>の種類のイベント<xref:System.ComponentModel.ListChangedType.ItemChanged>を通じてその<xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A>プロパティ。

  > [!NOTE]
  > 実装する必要があります、 <xref:System.ComponentModel.IRaiseItemChangedEvents> 、データ ソースは、前に説明した一覧イベントを変換するプロパティを提供しとの対話は、<xref:System.Windows.Forms.BindingSource>コンポーネント。 それ以外の場合、<xref:System.Windows.Forms.BindingSource>プロパティをパフォーマンスが低下リスト イベントへの変換を実行することもできます。

- <xref:System.ComponentModel.ISupportInitialize> インターフェイス

  実装するコンポーネント、<xref:System.ComponentModel.ISupportInitialize>インターフェイスは、プロパティの設定および依存するプロパティの初期化中にバッチ最適化の利点があります。 <xref:System.ComponentModel.ISupportInitialize> 2 つのメソッドが含まれています。

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> そのオブジェクトの初期化の開始を通知します。

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> そのオブジェクトの初期化が終了した後に通知します。

- <xref:System.ComponentModel.ISupportInitializeNotification> インターフェイス

  実装するコンポーネント、<xref:System.ComponentModel.ISupportInitializeNotification>インターフェイスの実装も、<xref:System.ComponentModel.ISupportInitialize>インターフェイス。 このインターフェイスを使用すると、その他の通知<xref:System.ComponentModel.ISupportInitialize>コンポーネント初期化が完了します。 <xref:System.ComponentModel.ISupportInitializeNotification>インターフェイスには、2 つのメンバーが含まれています。

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> 返します、`boolean`コンポーネントが初期化されているかどうかを示す値。

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> 発生したときに<xref:System.ComponentModel.ISupportInitialize.EndInit%2A>が呼び出されます。

- <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイス

  このインターフェイスを実装するクラスは、プロパティ値のいずれかが変更されたときにイベントを発生させる型です。 このインターフェイスは、コントロールのプロパティごとに変更イベントを持つパターンを置き換えるように設計されています。 使用すると、 <xref:System.ComponentModel.BindingList%601>、ビジネス オブジェクトを実装する必要があります、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスと、BindingList\`1 に変換されます<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>イベント<xref:System.ComponentModel.BindingList%601.ListChanged>の種類のイベント<xref:System.ComponentModel.ListChangedType.ItemChanged>します。

  > [!NOTE]
  > 変更の通知をバインドされているクライアントとデータ間のバインドで発生ソースにバインドされたデータ ソースの種類を実装するか、 <xref:System.ComponentModel.INotifyPropertyChanged> (推奨) インターフェイスを提供できます*propertyName* `Changed`バインドの型がイベントには、両方を行うことはできません。

### <a name="interfaces-for-implementation-by-component-authors"></a>コンポーネント作成者が実装するインターフェイス

以下のインターフェイスは、Windows フォーム データ バインディング エンジンが使用するように設計されています。

- <xref:System.Windows.Forms.IBindableComponent> インターフェイス

  このインターフェイスを実装するクラスは、データ バインディングをサポートするコントロール以外のコンポーネントです。 このクラスは、データ バインディングとバインド コンテキストを使用して、コンポーネントを返します、<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>と<xref:System.Windows.Forms.IBindableComponent.BindingContext%2A>このインターフェイスのプロパティ。

  > [!NOTE]
  > コンポーネントから継承している場合<xref:System.Windows.Forms.Control>、実装する必要はありません、<xref:System.Windows.Forms.IBindableComponent>インターフェイス。

- <xref:System.Windows.Forms.ICurrencyManagerProvider> インターフェイス

  実装するクラス、<xref:System.Windows.Forms.ICurrencyManagerProvider>インターフェイスは、独自に提供するコンポーネント<xref:System.Windows.Forms.CurrencyManager>この特定のコンポーネントに関連付けられているバインドを管理します。 カスタムへのアクセス<xref:System.Windows.Forms.CurrencyManager>によって提供される、<xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>プロパティ。

  > [!NOTE]
  > 継承するクラスを<xref:System.Windows.Forms.Control>管理バインドを使用して自動的にその<xref:System.Windows.Forms.Control.BindingContext%2A>プロパティを実装する必要があるため場合、<xref:System.Windows.Forms.ICurrencyManagerProvider>非常にまれです。

## <a name="see-also"></a>関連項目

- [データ連結と Windows フォーム](data-binding-and-windows-forms.md)
- [方法: Windows フォームに単純バインド コントロールを作成する](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)
