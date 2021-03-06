---
title: PIM で Azure AD ロールのアクセスをレビューする - Azure AD | Microsoft Docs
description: Azure AD Privileged Identity Management (PIM) で Azure Active Directory ロールのアクセス レビューを実施する方法を説明します。
services: active-directory
documentationcenter: ''
author: curtand
manager: daveba
editor: ''
ms.service: active-directory
ms.topic: conceptual
ms.workload: identity
ms.subservice: pim
ms.date: 10/22/2019
ms.author: curtand
ms.custom: pim
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76eccb5d62b68865b7a117312be62753f203e2cb
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "73847092"
---
# <a name="review-access-to-azure-ad-roles-in-privileged-identity-management"></a>Privileged Identity Management で Azure AD ロールのアクセスをレビューする

Privileged Identity Management (PIM) を使用すると、企業が Azure Active Directory (AD) や他の Microsoft オンライン サービス (Office 365 や Microsoft Intune など) 内のリソースへの特権アクセスを管理する方法が簡略化されます。 この記事に記載された手順を行うと、割り当てられたロールを問題なく自己レビューできます。

既に管理者ロールに割り当てられているユーザーは、組織の特権ロール管理者から、自分の業務にそのロールがまだ必要であるかどうかを定期的に確認するよう求められることがあります。 リンクが記載された電子メールが届く場合もあれば、直接 [Azure portal](https://portal.azure.com) にアクセスして開始することもできます。

特権ロール管理者またはグローバル管理者としてアクセス レビューに関心がある場合は、 [アクセス レビューを開始する方法](pim-how-to-start-security-review.md)に関するページで詳細を確認できます。

## <a name="add-a-pim-dashboard-tile"></a>PIM ダッシュボード タイルを追加する

Azure portal で Azure AD Privileged Identity Management サービスをダッシュボードにピン留めしていない場合、まず、以下の手順を行ってください。

1. [Azure portal](https://portal.azure.com/) にサインインする
2. Azure Portal の右上隅に表示されているユーザー名をクリックし、操作するディレクトリを選択します。
3. **[すべてのサービス]** を選択し、[フィルター] ボックスを使用して **Azure AD Privileged Identity Management** を検索します。
4. **[ダッシュボードにピン留めする]** チェック ボックスをオンにし、 **[作成]** をクリックします。 Privileged Identity Management アプリケーションが起動します。

## <a name="approve-or-deny-access"></a>アクセスの承認または拒否

アクセスを承認または拒否する場合、このロールをまだ使用するかどうかをレビュー担当者にのみ通知します。 ロールにとどまる場合は **[承認]** を選択します。また、アクセスが不要な場合は **[拒否]** を選択します。 レビュー担当者が結果を適用するまで、状態はすぐに変更されません。
アクセス レビューを検索して完了するには、次の手順に従います。

1. Privileged Identity Management サービスで、 **[特権アクセスのレビュー]** を選択します。 保留中のアクセス レビューがある場合は、Azure AD の **[アクセス レビュー]** ページが表示されます。
2. 完了するレビューを選択します。
3. レビューを作成した場合を除き、レビューで唯一のユーザーとして表示されます。 名前の横にあるチェック マークを選択します。
4. **[承認]** または **[拒否]** のいずれかを選択します。 **[理由の提供]** テキスト ボックスで決定の理由を含めることが必要になる場合があります。  
5. **[Azure AD ロールのレビュー]** ブレードを閉じます。

<!--Every topic should have next steps and links to the next logical set of content to keep the customer engaged-->
## <a name="next-steps"></a>次のステップ

- [PIM で自分の Azure リソース ロールのアクセス レビューを実行する](pim-resource-roles-perform-access-review.md)
