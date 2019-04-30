---
title: パッケージ化とカスタム My 拡張 (Visual Basic) の配置
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 4212f58c39f63be6ba20c3b79e5d9c98d0615c5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014207"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>パッケージ化し、カスタム My 拡張 (Visual Basic) のデプロイ

Visual Basic では、ユーザー設定を展開するための簡単な方法`My`Visual Studio テンプレートを使用して名前空間の拡張機能。 対象のプロジェクト テンプレートを作成する場合、`My`拡張機能は、新しいプロジェクトの種類の不可欠なカスタムを含めることができますのみ`My`テンプレートをエクスポートする場合は、プロジェクトで拡張機能のコード。 プロジェクト テンプレートをエクスポートする方法の詳細については、次を参照してください。[方法。プロジェクト テンプレートを作成](/visualstudio/ide/how-to-create-project-templates)です。

場合、カスタム`My`拡張機能が 1 つのコード ファイルに、ユーザーは、あらゆる種類の Visual Basic プロジェクトに追加できる項目テンプレートとして、ファイルをエクスポートすることができます。 追加の機能と、カスタムの動作を有効にする項目テンプレートをカスタマイズすることができますし`My`Visual Basic プロジェクトで拡張機能。 これらの機能を以下に示します。

- ユーザーが、カスタム管理できるように`My`から拡張機能、**マイ拡張**Visual Basic のプロジェクト デザイナーのページ。

- 自動的に追加するカスタム`My`拡張機能と、指定したアセンブリへの参照がプロジェクトに追加します。

- 非表示、`My`拡張機能の項目テンプレートを**項目の追加**ダイアログ ボックスがプロジェクト項目の一覧には含まれません。

このトピックでは、カスタムのパッケージ化する方法を説明`My`拡張機能から管理可能な非表示の項目テンプレートとして、**マイ拡張**Visual Basic のプロジェクト デザイナーのページ。 カスタム`My`拡張機能追加することも自動的に指定したアセンブリへの参照がプロジェクトに追加されたときにします。

## <a name="create-a-my-namespace-extension"></a>作成、My 名前空間拡張

カスタムの配置パッケージの作成の最初のステップ`My`拡張機能は、1 つのコード ファイルとして拡張機能を作成します。 詳細およびカスタムを作成する方法についてガイダンス`My`拡張機能を参照してください[Visual Basic の My Namespace の拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)します。

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>エクスポートする項目のテンプレートと My 名前空間拡張

含むコード ファイルを作成したら、`My`名前空間の拡張機能は、Visual Studio 項目テンプレートとして、コード ファイルをエクスポートすることができます。 Visual Studio 項目テンプレートとしてファイルにエクスポートする方法の詳細については、次を参照してください。[方法。項目テンプレートを作成](/visualstudio/ide/how-to-create-item-templates)です。

> [!NOTE]
> 場合、`My`名前空間の拡張機能は、特定のアセンブリに対する依存関係を持つ、自動的にインストールするように項目テンプレートをカスタマイズすることができます、`My`そのアセンブリへの参照が追加されたときに名前空間の拡張機能。 その結果、コード ファイルを Visual Studio 項目テンプレートとしてエクスポートするときに、アセンブリ参照を除外するされます。

## <a name="customize-the-item-template"></a>項目テンプレートをカスタマイズします。

項目テンプレートを管理することができます、**マイ拡張**Visual Basic のプロジェクト デザイナーのページ。 項目テンプレートを指定したアセンブリへの参照がプロジェクトに追加されたときに自動的に追加することもできます。 これらのカスタマイズを有効にするのには、テンプレート、CustomData ファイルと呼ばれる、新しいファイルに追加し、.vstemplate ファイルで XML を新しい要素を追加します。

### <a name="add-the-customdata-file"></a>CustomData ファイルを追加します。

CustomData ファイルは、ファイル名拡張子を持つテキスト ファイルです。CustomData (ファイル名設定できます任意の値に、テンプレートに意味のある) XML を格納しているとします。 CustomData ファイル内の XML を含める Visual Basic の指示、`My`ユーザーの使用時に拡張子、**マイ拡張**Visual Basic のプロジェクト デザイナーのページ。 必要に応じて追加することができます、<`AssemblyFullName>` CustomData ファイルの XML を属性します。 これにより、ユーザー設定を自動的にインストールする Visual Basic`My`特定のアセンブリへの参照時に拡張子がプロジェクトに追加します。 CustomData ファイルを作成する任意のテキスト エディターまたは XML エディターを使用し、項目テンプレートの圧縮フォルダー (.zip ファイル) に追加できます。

たとえば、次の XML では Microsoft.VisualBasic.PowerPacks.Vs.dll アセンブリへの参照時に、Visual Basic プロジェクトの My の拡張機能フォルダーにテンプレート項目を追加する CustomData ファイルの内容は、プロジェクトに追加されます。

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

CustomData ファイルを含む、<`VBMyExtensionTemplate>`を次の表に記載されている属性を持つ要素。

|属性|説明|
|---|---|
|`ID`|必須。 拡張機能の一意の識別子。 この ID を持つ拡張機能は、プロジェクトに既に追加されている場合、もう一度追加するない、ユーザーが求められます。|
|`Version`|必須。 項目テンプレートのバージョン番号です。|
|`AssemblyFullName`|任意。 アセンブリ名。 追加するユーザーの入力を求め、このアセンブリへの参照がプロジェクトに追加されると、`My`この項目テンプレートからの拡張機能。|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>追加、 \<CustomDataSignature > 要素を .vstemplate ファイル

として、Visual Studio 項目テンプレートを識別するために、`My`名前空間の拡張項目テンプレートの .vstemplate ファイルを変更することも必要があります。 追加する必要があります、`<CustomDataSignature>`要素を`<TemplateData>`要素。 `<CustomDataSignature>`要素は、テキストを含める必要があります`Microsoft.VisualBasic.MyExtension`次の例のようにします。

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

圧縮されたフォルダー (.zip ファイル) 内のファイルを直接変更することはできません。 .Vstemplate ファイルを圧縮フォルダーからコピー、変更、および、更新されたコピーを使用して、圧縮フォルダーの .vstemplate ファイルを置換する必要があります。

次の例を含む .vstemplate ファイルの内容を示しています、`<CustomDataSignature>`要素を追加します。

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a>テンプレートをインストールします。

テンプレートをインストールするには、圧縮フォルダーをコピーすることができます (*.zip*ファイル)、Visual Basic 項目テンプレート フォルダーにします。 既定では、ユーザー項目テンプレートに *%USERPROFILE%\Documents\Visual Studio\<バージョン\>\Templates\ItemTemplates\Visual Basic*します。 また、Visual Studio インストーラーとしてテンプレートを公開することができます (*.vsi*) ファイル。

## <a name="see-also"></a>関連項目

- [Visual Basic における My 名前空間の拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [Visual Basic アプリケーション モデルの拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [[マイ拡張] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
