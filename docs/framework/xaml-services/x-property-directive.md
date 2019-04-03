---
title: x:Property ディレクティブ
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: ab25381769e7001f7f48d73e717b5f495da90dfa
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836293"
---
# <a name="xproperty-directive"></a>x:Property ディレクティブ
マークアップで XAML プロパティを宣言します。  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`className`|XAML 運用環境のバッキング クラスまたは部分クラスの名前。|  
|`propertyName`|定義されるプロパティのメンバーの名前。|  
|`propertyType`|このプロパティの型を指定する型名 (またはその他の文字列の形式、フレームワーク固有)。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework XAML サービス実装では、 `x:Property` には直接の型のバッキングはありませんが、<xref:System.Windows.Markup.PropertyDefinition> クラスによってサポートされています。 XAML ノード ストリームでは、`x:Property` 要素は、XAML 言語の XAML 名前空間から `Property` という名前のメンバーとして表されます。 メンバー `Property` は、マークアップによって宣言された属性を保持します。  
  
 `Name` と `Type` の意味は .NET Framework XAML サービス レベルでは割り当てられません。 これらは、特定のフレームワークによって課される可能性がある規則の下で後に解釈される文字列の値として、初期の XAML ノード ストリームに格納されます。 意味は、実装によって、XAML の名前および XAML 型の意味と揃えるか、バッキング型のシステムでのみ有効になることがあります。  
  
 マークアップでメンバーの定義を指定する手段として `x:Members` の実用的な使用法をサポートするため、メンバーを変更可能なクラスに関連付ける必要があります。 目的とするモデルは、`x:Members` が `x:Class` を指定する型のメンバーとして存在することです。 ただし、型とメンバーを関連付けたり、動的メンバーの定義を作成したりするメカニズムは、.NET Framework XAML サービス レベルではサポートされません。 これは、XAML のメンバーの定義をサポートするアプリケーション モデルがある個々のフレームワークに残されています。 一般に、XAML をマークアップ コンパイルするとともに、XAML と分離コードの統合または純粋な XAML からのアセンブリの生成を行う MSBUILD のビルド操作が、この機能をサポートするために必要です。  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>Windows Workflow Foundation の x:Property  
 Windows Workflow Foundation では、 `x:Property` は、全体が XAML で構成されるカスタム アクティビティのメンバーや、分離コードを含むアクティビティ デザイナーの XAML で定義された動的メンバーを定義します。 `x:Class` は、XAML の運用環境のルート要素にも指定する必要があります。 これは、.NET Framework XAML サービス レベルの要件ではありませんが、全般にカスタム アクティビティと Windows Workflow Foundation の XAML をサポートする MSBUILD のビルド アクションによって XAML の運用環境が読み込まれるときの要件になります。 Windows Workflow Foundation がその目的とする値として、純粋な XAML 型名を使用しない、 `x:Property` `Type`属性し、代わりにここで説明されていない規則を使用します。 詳細については、[DynamicActivity の作成](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100))を参照してください。
