---
title: .NET Framework アプリケーションにおける COM 相互運用性
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 1c484ae948c247a97dd57539e3b0be263736aceb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348745"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework アプリケーションにおける COM 相互運用性 (Visual Basic)

When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory. A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed. A COM object is located in unmanaged memory and is not expected to move to another memory location. Visual Studio and the .NET Framework provide tools to control the interaction of these managed and unmanaged components. For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).

In addition to using COM objects in .NET applications, you may also want to use Visual Basic to develop objects accessible from unmanaged code through COM.

The links on this page provide details on the interactions between COM and .NET Framework objects.

## <a name="related-sections"></a>関連項目

| | |
|---------|---------|
| [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md) | Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects. |
| [アンマネージ コードとの相互運用](../../../framework/interop/index.md) | Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study. |
| [COM ラッパー](../../../standard/native-interop/com-wrappers.md) | Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods. |
| [高度な COM 相互運用性](../../../framework/interop/index.md) | Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling. |
| [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md) | Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly. |
