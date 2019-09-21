---
title: Exception Thrown_V1 ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91abd9e6f31380b7e8cd3df1a14aa5c5722901ba
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046511"
---
# <a name="exception-thrown_v1-etw-event"></a>Exception Thrown_V1 ETW イベント
このイベントは、スローされる例外に関する情報をキャプチャします。  
  
 イベントが発生するキーワードとイベントのレベルを次の表に示します (詳細については、「 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)」を参照してください)。  
  
|イベントを発生させるキーワード|レベル|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|警告 (2)|  
  
 次の表にイベント情報を示します。  
  
|イベント|イベント ID|いつ発生するか|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|マネージド例外がスローされます。|  
  
 次の表にイベント データを示します。  
  
|フィールド名|データ型|説明|  
|----------------|---------------|-----------------|  
|例外の種類|win:UnicodeString|例外の種類 (`System.NullReferenceException` など)。|  
|例外メッセージ|win:UnicodeString|実際の例外メッセージ。|  
|EIPCodeThrow|win:Pointer|例外が発生した命令ポインター。|  
|ExceptionHR|win:UInt32|例外 [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679)。|  
|ExceptionFlags|win:UInt16|0x01HasInnerException (Visual Basic ドキュメントの「 [CLR ETW イベント](clr-etw-events.md)」を参照してください)。<br /><br /> 除くIsNestedException.<br /><br /> 0x04IsRethrownException.<br /><br /> 0x08IsCorruptedStateException (プロセスの状態が破損していることを示します。「MSDN で[破損状態の例外を処理](https://go.microsoft.com/fwlink/?LinkId=179681)する」を参照してください)。<br /><br /> 0x10IsCLSCompliant (から<xref:System.Exception>派生する例外は cls に準拠していますが、それ以外の場合は cls に準拠していません)。|  
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|  
  
## <a name="see-also"></a>関連項目

- [CLR ETW イベント](clr-etw-events.md)
