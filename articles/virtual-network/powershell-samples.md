---
title: 仮想ネットワーク用の Azure PowerShell サンプル
description: 仮想ネットワーク用の Azure PowerShell サンプル。
services: virtual-network
documentationcenter: virtual-network
author: KumudD
manager: twooley
editor: ''
tags: ''
ms.assetid: ''
ms.service: virtual-network
ms.devlang: na
ms.topic: sample
ms.tgt_pltfrm: ''
ms.workload: infrastructure
ms.date: 07/15/2019
ms.author: kumud
ms.openlocfilehash: de752cdacf17193d5be95b2b9f887938ace2d50f
ms.sourcegitcommit: 0947111b263015136bca0e6ec5a8c570b3f700ff
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "74091881"
---
# <a name="azure-powershell-samples-for-virtual-network"></a>仮想ネットワーク用の Azure PowerShell サンプル

次の表には、Azure PowerShell スクリプトへのリンクが含まれています。

| | |
|----|----|
| [多層アプリケーション用の仮想ネットワークの作成](./scripts/virtual-network-powershell-sample-multi-tier-application.md) | フロントエンド サブネットとバックエンド サブネットを含む仮想ネットワークを作成します。 フロントエンド サブネットへのトラフィックは HTTP に制限され、バックエンド サブネットへのトラフィックは SQL、ポート 1433 に制限されます。 |
| [2 つの仮想ネットワークのピアリング](./scripts/virtual-network-powershell-sample-peer-two-virtual-networks.md) | 同じリージョンに 2 つの仮想ネットワークを作成し、接続します。 |
| [ネットワーク仮想アプライアンス経由のトラフィックのルーティング](./scripts/virtual-network-powershell-sample-route-traffic-through-nva.md) | フロントエンド サブネットとバックエンド サブネットを含む仮想ネットワークと、2 つのサブネット間でトラフィックをルーティングできる VM を作成します。 |
| [VM ネットワークの着信トラフィックおよび送信トラフィックのフィルター処理](./scripts/virtual-network-powershell-sample-filter-network-traffic.md) | フロントエンド サブネットとバックエンド サブネットを含む仮想ネットワークを作成します。 フロントエンド サブネットへの着信ネットワーク トラフィックは、HTTP と HTTPS に制限されます。 バックエンド サブネットからインターネットへの送信トラフィックは許可されません。 |
|[Basic Load Balancer を使用した IPv4 と IPv6 のデュアル スタック仮想ネットワークの構成](./scripts/virtual-network-powershell-sample-ipv6-dual-stack.md)|2 つの VM と IPv4 および IPv6 のパブリック IP アドレスを使用した Azure Basic Load Balancer によるデュアル スタック (IPv4+IPv6) の仮想ネットワークを展開します。 |
|[Standard Load Balancer を使用した IPv4 と IPv6 のデュアル スタック仮想ネットワークの構成](./scripts/virtual-network-powershell-sample-ipv6-dual-stack-standard-load-balancer.md)|2 つの VM と IPv4 および IPv6 のパブリック IP アドレスを使用した Azure Standard Load Balancer によるデュアル スタック (IPv4+IPv6) の仮想ネットワークを展開します。 |
