---
title: アプリケーション パフォーマンスの計画
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
ms.openlocfilehash: 70dda68112d47d3e5a0609a5df7696920477c698
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210205"
---
# <a name="planning-for-application-performance"></a>アプリケーション パフォーマンスの計画
パフォーマンスの目標を達成できるパフォーマンス戦略を開発するかによって異なります。 計画は、任意の製品の開発の最初のステージです。 このトピックでは、良好なパフォーマンスの戦略を開発するためのいくつかの非常に単純な規則について説明します。  
  
## <a name="think-in-terms-of-scenarios"></a>シナリオの観点から考える  
 シナリオを使用するアプリケーションの重要なコンポーネントに注目します。 シナリオは、一般に、顧客、および競争力のある製品から派生します。 常にお客様を調査し、何に引き付け、製品、および競合他社の製品について確認します。 お客様のフィードバックは、アプリケーションの主なシナリオを特定するのに役立ちます。 たとえば、起動時に使用されるコンポーネントをデザインする場合は、アプリケーションの起動時に、コンポーネントを 1 回だけ呼び出すこと可能性が。 起動時間は、重要なシナリオになります。 他の主要なシナリオの例では、アニメーション シーケンスの場合、目的のフレーム レートをするか、最大ワーキング セットは、アプリケーションに使用できる可能性があります。  
  
## <a name="define-goals"></a>目標を定義します。  
 目標を使用して、アプリケーションのパフォーマンスが速くまたは遅くするかどうかを判断するのに役立ちます。 すべてのシナリオでは、目標を定義する必要があります。 定義するすべてのパフォーマンスの目標は、顧客の期待に基づく必要があります。 セットのパフォーマンスのアプリケーション開発の早い段階で目標サイクルで多くの未解決の問題が引き続き発生するときに難しい場合があります。 しかし、当初の目標を設定し、それをしないより目標に後で変更することをお勧めします。  
  
## <a name="understand-your-platform"></a>プラットフォームを理解します。  
 測定、調査、アプリケーションの開発サイクル中に調整/修正のサイクルを常に維持します。 開発サイクルの最後に、最初からは、信頼性の高い、安定した環境でアプリケーションのパフォーマンスを測定する必要があります。 外部要因による変動を避ける必要があります。 例: パフォーマンスをテストするときにウイルス対策ソフトウェアや SMS などの任意の自動更新を無効にする、テスト結果のパフォーマンスに影響しないようにする必要があります。 アプリケーションのパフォーマンスを測定する最も大きな強化点の原因となる変更を特定する必要があります。 アプリケーションを変更した後、もう一度サイクルを開始します。  
  
## <a name="make-performance-tuning-an-iterative-process"></a>パフォーマンス チューニングを反復処理  
 使用する各機能の相対的なコストをおく必要があります。 たとえば、Microsoft .NET Framework でのリフレクションの使用は一般的にパフォーマンス、コンピューティング リソースの観点から処理を要する、慎重に使用するためです。 限りません、リフレクションの使用を回避するために使用する機能のパフォーマンス ニーズと、アプリケーションのパフォーマンス要件のバランスを取るように注意しておく必要があることだけです。  
  
## <a name="build-towards-graphical-richness"></a>グラフィカルな豊富な機能を目指す  
 キーの手法を実現するスケーラブルなアプローチを作成するため[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションのパフォーマンスは、グラフィカルな豊富な機能と複雑さに構築します。 常にシナリオの目標を達成するために最低のパフォーマンスの処理を要するリソースの使用を開始します。 これらの目標を達成すると、シナリオの目標を常に念頭に置きながらパフォーマンス負荷の高い機能、複数を使用して豊かなグラフィックス ビルドします。 ただし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]非常に豊富なプラットフォームは、非常に豊かなグラフィック機能を提供します。 考慮せずパフォーマンス負荷の高い機能を使用すると、アプリケーション全体のパフォーマンスに悪影響を与えることができます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールは、そのコントロールの動作を変更しない中に、それらの外観のカスタマイズを広範囲に及ぶようにすることで本質的に拡張可能です。 スタイル、データ テンプレート、およびコントロール テンプレートの利用して、作成して段階的にカスタマイズ可能な進化[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]パフォーマンスの要件に対応します。  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)
- [ハードウェアの活用](optimizing-performance-taking-advantage-of-hardware.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
- [2D グラフィックスとイメージング](optimizing-performance-2d-graphics-and-imaging.md)
- [オブジェクトの動作](optimizing-performance-object-behavior.md)
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [[テキスト]](optimizing-performance-text.md)
- [データ バインディング](optimizing-performance-data-binding.md)
- [パフォーマンスに関するその他の推奨事項](optimizing-performance-other-recommendations.md)
