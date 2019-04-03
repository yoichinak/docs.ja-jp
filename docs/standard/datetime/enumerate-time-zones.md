---
title: '方法: コンピューター上に存在するタイム ゾーンを列挙します。'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 697cd40482aee73fd150359acb710ffc258c3df2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518411"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>方法: コンピューター上に存在するタイム ゾーンを列挙します。

指定されたタイム ゾーンを正しく処理するには、そのタイム ゾーンに関する情報がシステムで使用できる必要があります。 Windows XP および Windows Vista オペレーティング システムでは、この情報は、レジストリに格納します。 しかし、世界中に存在するタイム ゾーンの合計数は大きいものの、レジストリにはそれらの一部に関する情報しか含まれません。 さらに、レジストリ自体は、内容が意図的に、および誤って変更される可能性がある動的な構造です。 その結果、アプリケーションは、特定のタイム ゾーンがシステムで定義され、使用できると常に想定することができません。 タイム ゾーン情報のアプリケーションを使用する多くのアプリケーションの最初の手順は、必要なタイム ゾーンがローカル システムで使用できるかどうかを判断する、またはタイム ゾーンの一覧をユーザーに提供して選択させることです。 これには、アプリケーションがローカル システムで定義されているタイム ゾーンを列挙する必要があります。

> [!NOTE]
> アプリケーションがローカル システムで定義されていない特定のタイム ゾーンの存在に依存している場合、アプリケーションはその存在を確認しますタイム ゾーンの情報をシリアル化および。 アプリケーションのユーザーが選択できるように、タイム ゾーンは、リスト コントロールに追加できます。 詳細については、[方法。埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)と[方法。埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)を参照してください。

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>ローカル システムに存在するタイム ゾーンを列挙するには

1. <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> メソッドを呼び出します。 メソッドはジェネリック型を返します<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>のコレクション<xref:System.TimeZoneInfo>オブジェクト。 コレクション内のエントリは並んで、<xref:System.TimeZoneInfo.DisplayName%2A>プロパティ。 例:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. 個々 の列挙<xref:System.TimeZoneInfo>を使用してコレクション内のオブジェクトを`foreach`ループ (c#) または`For Each`.`Next` (Visual Basic の場合) ではループし、各オブジェクトに対して必要な処理を実行します。 たとえば、次のコードを列挙、<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>のコレクション<xref:System.TimeZoneInfo>で返される手順 1 のオブジェクトし、コンソールでは、各タイム ゾーンの表示名を一覧表示されます。

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>ローカル システムに存在するタイム ゾーンの一覧をユーザーに表示するには

1. <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> メソッドを呼び出します。 メソッドはジェネリック型を返します<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>のコレクション<xref:System.TimeZoneInfo>オブジェクト。

2. 手順 1. で返されるコレクションに割り当てる、`DataSource`プロパティの Windows フォームや ASP.NET リスト コントロール。

3. 取得、<xref:System.TimeZoneInfo>ユーザーが選択したオブジェクト。

Windows アプリケーションを例に示します。

## <a name="example"></a>例

例では、リスト ボックスで、システムで定義されているタイム ゾーンを表示する Windows アプリケーションを起動します。 例では、値を含むダイアログ ボックスを表示し、<xref:System.TimeZoneInfo.DisplayName%2A>ユーザーが選択したタイム ゾーン オブジェクトのプロパティ。

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

最もリスト コントロール (など、<xref:System.Windows.Forms.ListBox?displayProperty=nameWithType>または<xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType>コントロール) をオブジェクト変数のコレクションに割り当てられるように、`DataSource`プロパティをそのコレクションを実装している限り、<xref:System.Collections.IEnumerable>インターフェイス。 (ジェネリック<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>クラスは、この)。コレクションには、個々 のオブジェクトを表示するには、このコントロールはそのオブジェクトを呼び出します。`ToString`オブジェクトを表すために使用する文字列を抽出するメソッド。 場合<xref:System.TimeZoneInfo>、オブジェクト、`ToString`メソッドを返します、<xref:System.TimeZoneInfo>オブジェクトの表示名 (の値、<xref:System.TimeZoneInfo.DisplayName%2A>プロパティ)。

> [!NOTE]
> リスト コントロールの呼び出し、オブジェクトのため、`ToString`メソッドのコレクションを割り当てることができます<xref:System.TimeZoneInfo>コントロールにオブジェクトがある各オブジェクトについて、わかりやすい名前を表示し、取得、コントロール、<xref:System.TimeZoneInfo>ユーザーが選択したオブジェクト。 コレクション内の各オブジェクトの文字列を抽出する、コントロールにさらに割り当てられているコレクションに文字列を割り当てる必要はなくなります`DataSource`プロパティは、ユーザーが選択すると、文字列を取得し、この文字列を使用して、オブジェクトの抽出その it について説明します。 

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* System.Core.dll への参照をプロジェクトに追加します。

* 次の名前空間は、インポートします。

  <xref:System> (c# コードで)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [方法: 埋め込みリソースにタイム ゾーンを保存します。](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [方法: 埋め込みリソースからタイム ゾーンを復元します。](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
