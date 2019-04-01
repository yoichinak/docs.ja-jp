---
title: /refout (C# コンパイラ オプション)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 06d21843c6e2d7aeb1858c3ce72426d080f73595
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410213"
---
# <a name="-refout-c-compiler-options"></a>/refout (C# コンパイラ オプション)

**-refout** オプションは、参照アセンブリを出力するファイル パスを指定します。 Emit API では、これを `metadataPeStream` に変換します。

## <a name="syntax"></a>構文

```console
-refout:filepath
```

## <a name="arguments"></a>引数

 `filepath` 参照アセンブリのファイル パス。 通常はプライマリ アセンブリのファイルパスと一致します。 (MSBuild で使用される) 推奨規則は、プライマリ アセンブリに相対する "ref/" サブ フォルダー内に参照アセンブリを配置することです。

## <a name="remarks"></a>解説

メタデータのみアセンブリには、1 つの `throw null` 本体で置き換えられたメソッド本体がありますが、匿名型を除くすべてのメンバーが含まれます。 (本体なしではなく) `throw null` 本体を使用する理由は、PEVerify を実行して渡せるようにするためです (そのためにメタデータの完全性を検証します)。

参照アセンブリには、アセンブリ レベルの `ReferenceAssembly` 属性が含まれます。 この属性は、ソースで指定できます (指定すると、コンパイラではこれを合成する必要がなくなります)。 この属性により、ランタイムで実行のための参照アセンブリの読み込みが拒否されます (ただし、リフレクションのみモードでは読み込むことができます)。 アセンブリにリフレクションするツールでは、参照アセンブリをリフレクションのみで読み込んでいることを確認する必要があります。そうでない場合、ランタイムから typeload エラーを受け取ります。

参照アセンブリは、メタデータのみアセンブリからさらにメタデータ (プライベート メンバー) を削除します。

- 参照アセンブリには、API サーフェスでそれが必要とする参照のみがあります。 実際のアセンブリには、特定の実装に関連するその他の参照がある場合があります。 たとえば、`class C { private void M() { dynamic d = 1; ... } }` の参照アセンブリは、`dynamic` に必要などの型も参照しません。
- プライベート関数のメンバー (メソッド、プロパティ、およびイベント) は、それらの削除がコンパイルに著しい影響を与えない場合に削除されます。 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性がない場合、内部関数メンバーに同じことを行います。
- ただし、すべての型 (プライベートまたは入れ子になった型を含む) は参照アセンブリで保持されます。 すべての属性が (内部属性も) 保持されます。
- すべての仮想メソッドが保持されます。 明示的なインターフェイスの実装が保持されます。 明示的に実装されたプロパティとイベントが保持されます (これらのアクセサーが仮想のため保持されます)。
- 構造体のすべてのフィールドが保持されます  (これは、post-C#-7.1 絞り込みの候補です)。

`-refout` オプションと [`-refonly`](refonly-compiler-option.md) オプションは同時に指定できません。

## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
