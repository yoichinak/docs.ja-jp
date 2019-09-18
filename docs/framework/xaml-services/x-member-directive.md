---
title: x:Member ディレクティブ
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: d3d023873aab2039913a78108440a2e2d4ea77fb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053736"
---
# <a name="xmember-directive"></a>x:Member ディレクティブ
マークアップで XAML メンバーを宣言します。  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    <x:Member Name="propertyName"/>  
    additionalMembers  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`className`|XAML 運用環境のバッキング クラスまたは部分クラスの名前。|  
|`memberName`|定義されるプロパティのメンバーの名前。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework XAML サービス実装では、 `x:Member` には直接の型のバッキングはありませんが、<xref:System.Windows.Markup.MemberDefinition> クラスによってサポートされています。 XAML ノード ストリームでは、`x:Member` 要素は、XAML 言語の XAML 名前空間から `Member` という名前のメンバーとして表されます。 メンバー `Member` は、マークアップによって宣言された属性を保持します。  
  
 `Name` と `Type` の意味は、.NET Framework XAML サービス レベルでは割り当てられません。 これらは、特定のフレームワークによって課される可能性がある規則の下で後に解釈される文字列の値として、初期の XAML ノード ストリームに格納されます。 意味は、実装によって、XAML の名前および XAML 型の意味と揃えるか、バッキング型のシステムでのみ有効になることがあります。  
  
 マークアップでメンバーの定義を指定する手段として `x:Members` の実用的な使用法をサポートするため、メンバーを変更可能なクラスに関連付ける必要があります。 目的とするモデルは、`x:Members` が `x:Class` を指定する型のメンバーとして存在することです。 ただし、型とメンバーを関連付けたり、動的メンバーの定義を作成したりするメカニズムは、.NET Framework XAML サービス レベルではサポートされません。 これは、XAML のメンバーの定義をサポートするアプリケーション モデルがある個々のフレームワークに残されています。 一般に、XAML をマークアップ コンパイルするとともに、XAML と分離コードの統合または純粋な XAML からのアセンブリの生成を行う MSBUILD のビルド操作が、この機能をサポートするために必要です。  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>Windows Workflow Foundation の x:Property  
 Windows Workflow Foundation では、 `x:Property` は、全体が XAML で構成されるカスタム アクティビティのメンバーや、分離コードを含むアクティビティ デザイナーの XAML で定義された動的メンバーを定義します。 `x:Class` は、XAML の運用環境のルート要素にも指定する必要があります。 これは、.NET Framework XAML サービス レベルの要件ではありませんが、全般にカスタム アクティビティと Windows Workflow Foundation の XAML をサポートする MSBUILD のビルド アクションによって XAML の運用環境が読み込まれるときの要件になります。 Windows Workflow Foundation は、 `x:Property` `Type`属性の意図された値として純粋な XAML 型名を使用しません。代わりに、ここに記載されていない規則が使用されます。 詳細については、「 [DynamicActivity の作成](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100))」を参照してください。
