---
title: Azure Media Services における LiveEvent の状態と課金 | Microsoft Docs
description: このトピックでは、Azure Media Services における LiveEvent の状態と課金について、その概要を説明します。
services: media-services
documentationcenter: ''
author: Juliako
manager: femila
editor: ''
ms.service: media-services
ms.workload: media
ms.tgt_pltfrm: na
ms.devlang: ne
ms.topic: article
ms.date: 10/24/2019
ms.author: juliako
ms.openlocfilehash: e4eee3b9f3f97bf7cd7a7b61425ec5c9a3a198ef
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "76543077"
---
# <a name="live-event-states-and-billing"></a>ライブ イベントの状態と課金

Azure Media Services のライブ イベントでは、その状態が**実行中**に遷移するとすぐに課金が開始されます。 サービスを通過するビデオがない場合でも課金されます。 ライブ イベントの課金を停止するには、ライブ イベントを停止する必要があります。 ライブ文字起こしはライブ イベントと同じ方法で課金されます。

[ライブ イベント](https://docs.microsoft.com/rest/api/media/liveevents)の **LiveEventEncodingType** を Standard または Premium1080p に設定した場合、入力フィードがなくなり、実行中の**ライブ出力**がなくなってから 12 時間後に、まだ**実行中**状態のライブ イベントがあれば、それらは Media Services によって自動的に停止されます。 ただし、ライブ イベントが**実行中**状態だった期間については課金されます。

> [!NOTE]
> パススルー ライブ イベントは自動的には停止しません。過剰な課金を防ぐためには、API で明示的に停止する必要があります。 

## <a name="states"></a>状態

ライブ イベントは、次の状態のいずれかになります。

|State|説明|
|---|---|
|**停止**| これは、ライブ イベント作成後の初期状態です (自動開始が true に設定された場合を除く)。この状態では、課金は行われません。 この状態で、ライブ イベントのプロパティを更新できますが、ストリーミングは許可されていません。|
|**開始中**| ライブ イベントが開始され、リソースが割り当てられています。 この状態では、課金は行われません。 この状態の間は、更新もストリーミングもできません。 エラーが発生した場合、ライブ イベントは停止状態に戻ります。|
|**実行中**| ライブ イベントのリソースが割り当てられ、取り込み URL とプレビュー URL も生成済みで、ライブ ストリームを受信することができます。 この時点で、課金がアクティブになります。 それ以上の課金を停止するには、ライブ イベント リソースの Stop を明示的に呼び出す必要があります。|
|**停止中**| ライブ イベントが停止され、リソースのプロビジョニングが解除されています。 この遷移状態では、課金は行われません。 この状態の間は、更新もストリーミングもできません。|
|**削除中**| ライブ イベントを削除しています。 この遷移状態では、課金は行われません。 この状態の間は、更新もストリーミングもできません。|

ライブ イベントを作成するときに、ライブ文字起こしを有効にすることを選択できます。 これを行うと、ライブ イベントが**実行中**の状態になると常に、ライブ文字起こしに対して課金されます。 ライブ イベントを通過するオーディオがない場合も課金されることに注意してください。

## <a name="next-steps"></a>次のステップ

- [ライブ ストリーミングの概要](live-streaming-overview.md)
- [ライブ ストリーミングのチュートリアル](stream-live-tutorial-with-api.md)
