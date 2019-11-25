---
title: SyncLock ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 0f430edce99513b0de9ef437d70648a128b336b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352818"
---
# <a name="synclock-statement"></a>SyncLock ステートメント
Acquires an exclusive lock for a statement block before executing the block.  
  
## <a name="syntax"></a>構文  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>指定項目  
 `lockobject`  
 必須です。 Expression that evaluates to an object reference.  
  
 `block`  
 省略可能です。 Block of statements that are to execute when the lock is acquired.  
  
 `End SyncLock`  
 Terminates a `SyncLock` block.  
  
## <a name="remarks"></a>Remarks  
 The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time. `SyncLock` prevents each thread from entering the block until no other thread is executing it.  
  
 The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously. If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.  
  
 A statement block protected by an exclusive lock is sometimes called a *critical section*.  
  
## <a name="rules"></a>ルール  
  
- Branching. You cannot branch into a `SyncLock` block from outside the block.  
  
- Lock Object Value. The value of `lockobject` cannot be `Nothing`. You must create the lock object before you use it in a `SyncLock` statement.  
  
     You cannot change the value of `lockobject` while executing a `SyncLock` block. The mechanism requires that the lock object remain unchanged.  
  
- You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.  
  
## <a name="behavior"></a>動作  
  
- Mechanism. When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression. When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.  
  
- Protected Data. If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it. This protects data that is shared among all the instances.  
  
     If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance. This protects data maintained by the individual instance.  
  
- Acquisition and Release. A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it. Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block. This is true even in the case of an unhandled exception.  
  
- Framework Calls. The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.  
  
## <a name="programming-practices"></a>Programming Practices  
 The `lockobject` expression should always evaluate to an object that belongs exclusively to your class. You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.  
  
 You should not use the `Me` keyword to provide a lock object for instance data. If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data. In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks. Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.  
  
 You should also not use the `Me.GetType` method to provide a lock object for shared data. This is because `GetType` always returns the same `Type` object for a given class name. External code could call `GetType` on your class and obtain the same lock object you are using. This would result in the two classes blocking each other from their `SyncLock` blocks.  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>説明  
 The following example shows a class that maintains a simple list of messages. It holds the messages in an array and the last used element of that array in a variable. The `addAnotherMessage` procedure increments the last element and stores the new message. Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.  
  
 If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`. In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>説明  
 The following example uses threads and `SyncLock`. As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number. You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>コメント  
  
## <a name="see-also"></a>関連項目

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [同期プリミティブの概要](../../../standard/threading/overview-of-synchronization-primitives.md)
