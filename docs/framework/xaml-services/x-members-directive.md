---
title: x:Members ディレクティブ
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: d23e6b459af932e0a6f69309f26a1cce70a9d256
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58034499"
---
# <a name="xmembers-directive"></a>x:Members ディレクティブ
親要素の x: クラスに適用されるマークアップで定義されているメンバーのセットを保持します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
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
|`oneOrMoreMembers`|メンバーの定義を表す 1 つまたは複数のオブジェクト要素。 通常、これらは`x:Property`object 要素。 「解説」を参照してください。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework XAML サービス実装ではありませんバッキング クラスまたはのメンバーの実装を基になる`x:Members`します。 `x:Members` 任意の型のメンバーとして存在できる特別な XAML メンバーです。 XAML ノード ストリームで`x:Members`という名前のメンバーとして表される`Members`、XAML 言語の XAML 名前空間から。 メンバー`Members`の読み取り専用のジェネリック リストを含む`Member`オブジェクト。 一般的なマークアップでは、個々 のメンバーとして指定されます`x:Property`プロパティ要素。 `x:Property` 型のプロパティを具体的には正確な型に割り当てることがあり`x:Member`します。 詳細については、[X:property ディレクティブ](x-property-directive.md)を参照してください。  
  
 マークアップでメンバーの定義を指定する手段として `x:Members` の実用的な使用法をサポートするため、メンバーを変更可能なクラスに関連付ける必要があります。 目的とするモデルは、`x:Members` が `x:Class` を指定する型のメンバーとして存在することです。 ただし、型とメンバーを関連付けたり、動的メンバーの定義を作成したりするメカニズムは、.NET Framework XAML サービス レベルではサポートされません。 これは、XAML のメンバーの定義をサポートするアプリケーション モデルがある個々のフレームワークに残されています。 一般に、XAML をマークアップ コンパイルするとともに、XAML と分離コードの統合または純粋な XAML からのアセンブリの生成を行う MSBUILD のビルド操作が、この機能をサポートするために必要です。  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>Windows Workflow Foundation の X:members  
 Windows Workflow foundation で`x:Members`XAML、または XAML 全体で構成されるカスタム アクティビティのメンバーを含む – 分離コードを含むアクティビティ デザイナーの動的メンバーを定義します。 `x:Class` は、XAML の運用環境のルート要素にも指定する必要があります。 これは、.NET Framework XAML サービス レベルの要件ではありませんが、全般にカスタム アクティビティと Windows Workflow Foundation の XAML をサポートする MSBUILD のビルド アクションによって XAML の運用環境が読み込まれるときの要件になります。 `x:Members` 宣言するオブジェクト要素のマークアップ内の最初の子要素である必要があります、`x:Class`します。
