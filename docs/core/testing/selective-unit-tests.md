---
title: 選択的単体テストの実行
description: .NET Core において dotnet test コマンドでフィルター式を使用して、選択的単体テストを実行する方法。
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: 50642126f3b470180ddd303ed4a2d2d90bfa5b8f
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728180"
---
# <a name="run-selective-unit-tests"></a>選択的単体テストの実行

.NET Core で `dotnet test` コマンドを使用することで、フィルター式を使用して、選択的テストを実行することができます。 この記事では、実行するテストをフィルター処理する方法を示します。 次の例では、`dotnet test` を使用します。 `vstest.console.exe` を使用している場合は、`--filter` を `--testcasefilter:` に置き換えます。

## <a name="character-escaping"></a>文字のエスケープ

`*nix` に感嘆符 (!) を含むフィルターを使用すると、`!` が予約されているために、エスケープが必要になります。 たとえば、名前空間に IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests` が含まれている場合、このフィルターではすべてのテストがスキップされます。
感嘆符の前にある円記号に注意してください。

ジェネリック型パラメーターで `FullyQualifiedName` 値にコンマを含める場合は、`%2C` を指定してコンマをエスケープします。 次に例を示します。

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a>MSTest

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestCategory("CategoryA")]
        [Priority(1)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [Priority(2)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| 正規表現 | 結果 |
| ---------- | ------ |
| `dotnet test --filter Method` | `FullyQualifiedName` に `Method` が含まれるテストを実行します。 `vstest 15.1+` で使用できます。 |
| `dotnet test --filter Name~TestMethod1` | 名前に `TestMethod1` が含まれるテストを実行します。 |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | クラス `MSTestNamespace.UnitTest1` 内にあるテストを実行します。<br>**注:** `ClassName` 値には名前空間があるため、`ClassName=UnitTest1` は機能しません。 |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | `MSTestNamespace.UnitTest1.TestMethod1` 以外のテストをすべて実行します。 |
| `dotnet test --filter TestCategory=CategoryA` | `[TestCategory("CategoryA")]` の注釈が付けられているテストを実行します。 |
| `dotnet test --filter Priority=2` | `[Priority(2)]` の注釈が付けられているテストを実行します。<br>

**条件演算子| と &amp; の使用**

| 正規表現 | 結果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | `FullyQualifiedName` に `UnitTest1` が含まれる、**または** `TestCategory` が `CategoryA` であるテストを実行します。 |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | `FullyQualifiedName` に `UnitTest1` が含まれ、**かつ** `TestCategory` が `CategoryA` であるテストを実行します。 |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | `FullyQualifiedName` に `UnitTest1` が含まれ、**かつ** `TestCategory` が `CategoryA` であるか、**または**、`Priority` が 1 であるテストを実行します。 |

## <a name="xunit"></a>xUnit

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "CategoryA")]
        [Trait("Priority", "1")]
        [Fact]
        public void Test1()
        {
        }

        [Trait("Priority", "2")]
        [Fact]
        public void Test2()
        {
        }
    }
}
```

| 正規表現 | 結果 |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | `XUnitNamespace.TestClass1.Test1` という 1 つのテストのみを実行します。 |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | `XUnitNamespace.TestClass1.Test1` 以外のテストをすべて実行します。 |
| `dotnet test --filter DisplayName~TestClass1` | 表示名に `TestClass1` が含まれるテストを実行します。 |

コード例では、特性をキー `Category` や `Priority` で定義すると、フィルター処理に使用できます。

| 正規表現 | 結果 |
| ---------- | ------ |
| `dotnet test --filter XUnit` | `FullyQualifiedName` に `XUnit` が含まれるテストを実行します。  `vstest 15.1+` で使用できます。 |
| `dotnet test --filter Category=CategoryA` | `[Trait("Category", "CategoryA")]` があるテストを実行します。 |

**条件演算子| と &amp; の使用**

| 正規表現 | 結果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | `FullyQualifiedName` に `TestClass1` が含まれる、**または** `Category` が `CategoryA` であるテストを実行します。 |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | `FullyQualifiedName` に `TestClass1` が含まれ、**かつ** `Category` が `CategoryA` であるテストを実行します。 |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | `FullyQualifiedName` に `TestClass1` が含まれ、**かつ** `Category` が `CategoryA` であるか、**または**、`Priority` が 1 であるテストを実行します。 |

## <a name="nunit"></a>NUnit

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Category("CategoryA")]
        [Property("Priority", 1)]
        [Test]
        public void TestMethod1()
        {
        }

        [Property("Priority", 2)]
        [Test]
        public void TestMethod2()
        {
        }
    }
}
```

| 正規表現 | 結果 |
| ---------- | ------ |
| `dotnet test --filter Method` | `FullyQualifiedName` に `Method` が含まれるテストを実行します。 `vstest 15.1+` で使用できます。 |
| `dotnet test --filter Name~TestMethod1` | 名前に `TestMethod1` が含まれるテストを実行します。 |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | クラス `NUnitNamespace.UnitTest1` 内にあるテストを実行します。<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | `NUnitNamespace.UnitTest1.TestMethod1` 以外のテストをすべて実行します。 |
| `dotnet test --filter TestCategory=CategoryA` | `[Category("CategoryA")]` の注釈が付けられているテストを実行します。 |
| `dotnet test --filter Priority=2` | `[Priority(2)]` の注釈が付けられているテストを実行します。<br>

**条件演算子| と &amp; の使用**

| 正規表現 | 結果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | `FullyQualifiedName` に `UnitTest1` が含まれる、**または** `TestCategory` が `CategoryA` であるテストを実行します。 |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | `FullyQualifiedName` に `UnitTest1` が含まれ、**かつ** `TestCategory` が `CategoryA` であるテストを実行します。 |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | `FullyQualifiedName` に `UnitTest1` が含まれ、**かつ** `TestCategory` が `CategoryA` であるか、**または**、`Priority` が 1 であるテストを実行します。 |

詳細については、[TestCase フィルター](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)に関するページを参照してください。
