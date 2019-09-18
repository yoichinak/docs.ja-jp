---
title: x:Members ディレクティブ
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: ca42079c1c40a8fb3b1ddfc8f4a6f742768fa9e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053762"
---
# <a name="xmembers-directive"></a>x:Members ディレクティブ
マークアップで定義されているメンバーのセットを保持します。これは、親要素の x:Class に適用されます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`className`|XAML 運用環境のバッキング クラスまたは部分クラスの名前。 「解説」を参照してください。|  
|`oneOrMoreMembers`|メンバー定義を表す1つ以上のオブジェクト要素。 通常、これらは`x:Property`オブジェクト要素です。 「解説」を参照してください。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework XAML サービスの実装では、のバッキングクラスまたは基になるメンバー `x:Members`の実装はありません。 `x:Members`は、任意の型のメンバーとして存在できる特殊な XAML メンバーです。 Xaml ノードストリーム`x:Members`では、は、xaml 言語の xaml `Members`名前空間からという名前のメンバーとして表されます。 メンバー `Members`には、オブジェクトの読み取り専用の`Member`ジェネリックリストが含まれています。 一般的なマークアップでは、個々の`x:Property`メンバーはプロパティ要素として指定されます。 `x:Property`は、型のプロパティ専用のより正確な型であり、 `x:Member`に割り当てることができます。 詳細については、「 [X:Property ディレクティブ](x-property-directive.md)」を参照してください。  
  
 マークアップでメンバーの定義を指定する手段として `x:Members` の実用的な使用法をサポートするため、メンバーを変更可能なクラスに関連付ける必要があります。 目的とするモデルは、`x:Members` が `x:Class` を指定する型のメンバーとして存在することです。 ただし、型とメンバーを関連付けたり、動的メンバーの定義を作成したりするメカニズムは、.NET Framework XAML サービス レベルではサポートされません。 これは、XAML のメンバーの定義をサポートするアプリケーション モデルがある個々のフレームワークに残されています。 一般に、XAML をマークアップ コンパイルするとともに、XAML と分離コードの統合または純粋な XAML からのアセンブリの生成を行う MSBUILD のビルド操作が、この機能をサポートするために必要です。  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>Windows Workflow Foundation 用の x:Members  
 Windows Workflow Foundation の場合`x:Members`は、xaml で完全に構成されるカスタムアクティビティのメンバー、または分離コードを持つアクティビティデザイナーの xaml で定義された動的メンバーが含まれます。 `x:Class` は、XAML の運用環境のルート要素にも指定する必要があります。 これは、.NET Framework XAML サービス レベルの要件ではありませんが、全般にカスタム アクティビティと Windows Workflow Foundation の XAML をサポートする MSBUILD のビルド アクションによって XAML の運用環境が読み込まれるときの要件になります。 `x:Members`は、を`x:Class`宣言するオブジェクト要素のマークアップ内の最初の子要素である必要があります。
