---
title: 実行可能インスタンス検出期間
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: 9652dd811f64e5324219b8aa0700ab8219edeeb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937957"
---
# <a name="runnable-instances-detection-period"></a>実行可能インスタンス検出期間
SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、実行可能またはアクティブ化可能なインスタンスを永続性データベースで検出します。 **実行可能インスタンス検出期間**SQL Workflow Instance Store のプロパティは、SQL Workflow Instance Store が実行可能またはアクティブ化可能なワークフローを検出するために検出タスクを実行するまでの期間を指定します前の検出サイクルの後に、永続性データベースのインスタンス。  
  
 このプロパティの間隔を短く設定すると、ワークフロー インスタンスに関連付けられたタイマーの期限切れと、イベントのシグナリングおよび後続のインスタンスの読み込みの間の時間が短くなります。 ただし、ホストにかかる処理の負荷も増えるため、永続的なタイマーやホスト エラーがまれなシナリオでは望ましくない場合があります。 プロパティの型は TimeSpan で、プロパティの値は hh:mm:ss の形式です。 このプロパティの最小値は 00:00:01 です。 プロパティの既定値は 00:00:05 です。  
  
 詳細については検出と、実行可能およびアクティブ化可能なワークフロー インスタンスをアクティブ化を参照してください[インスタンスのアクティベーション](instance-activation.md)します。
