---
title: -nostdlib (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: cf87d8d2ac4531142288a8637f7fbeb9139382ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545830"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# コンパイラ オプション)

**-nostdlib** は、System 名前空間の全体を定義する mscorlib.dll がインポートされないようにします。

## <a name="syntax"></a>構文

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>コメント

独自の System 名前空間およびオブジェクトを定義または作成する場合は、このオプションを使用します。

**/nostdlib** を指定しない場合、(**-nostdlib-** を指定したことと同じで) mscorlib.dll がプログラムにインポートされます。 **-nostdlib** を指定することは、**-nostdlib+** を指定することと同じです。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>このコンパイラ オプションを Visual Studio で使用するには

> [!NOTE]
> 次の手順は、Visual Studio 2015 (および以前のバージョン) のみに適用されます。 **Do not reference mscorlib.dll** ビルド プロパティは、Visual Studio 2017 には存在しません。

1. プロジェクトの **[プロパティ]** ページを開きます。

2. **[ビルド]** プロパティ ページをクリックします。

3. **[詳細設定]** ボタンをクリックします。

4. **[mscorlib.dll を参照しない]** プロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>」をご覧ください。

## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
