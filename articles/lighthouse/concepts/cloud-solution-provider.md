---
title: Cloud Solution Provider プログラムの考慮事項
description: CSP パートナーにとって、Azure の委任されたリソース管理は、粒度の細かいアクセス許可を実現することによってセキュリティと制御を強化する効果があります。
ms.date: 12/18/2019
ms.topic: conceptual
ms.openlocfilehash: 66ea74751f12a499a1e2d9e083497da31746e3c7
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "75456913"
---
# <a name="azure-lighthouse-and-the-cloud-solution-provider-program"></a>Azure Lighthouse と Cloud Solution Provider プログラム

[CSP (クラウド ソリューション プロバイダー)](https://docs.microsoft.com/partner-center/csp-overview) パートナーである場合、CSP プログラムを通じて顧客用に作成された Azure サブスクリプションには、[代理で管理 (AOBO)](https://channel9.msdn.com/Series/cspdev/Module-11-Admin-On-Behalf-Of-AOBO) 機能を使用してあらかじめアクセスできるようになっています。 このアクセスにより、顧客のサブスクリプションを直接サポートし、構成し、管理することができます。

[Azure Lighthouse](../overview.md) では、Azure の委任されたリソース管理と AOBO を併用できます。 より粒度の細かいアクセス許可をユーザーに使用できるようになるため、セキュリティが向上すると共に、不要なアクセスを減らすことにつながります。 また、ユーザーは、テナントに対する 1 つのログインを使用して、複数の顧客サブスクリプションにまたがって作業できるため、効率とスケーラビリティも向上します。

> [!TIP]
> 顧客のリソースを効果的に保護するため、Microsoft の[推奨セキュリティ プラクティス](recommended-security-practices.md)と[パートナーのセキュリティ要件](https://docs.microsoft.com/partner-center/partner-security-requirements)を確認し、それらに従うようにしてください。

## <a name="administer-on-behalf-of-aobo"></a>代理で管理 (AOBO)

AOBO を使用すると、テナント内の[管理エージェント](https://docs.microsoft.com/partner-center/permissions-overview#manage-commercial-transactions-in-partner-center-azure-ad-and-csp-roles) ロールを持つすべてのユーザーが、CSP プログラムを通じて貴社が作成した Azure サブスクリプションへの AOBO アクセス権を持つことになります。 顧客のサブスクリプションにアクセスする必要のあるすべてのユーザーは、このグループのメンバーである必要があります。 AOBO では、異なる顧客と共同作業を行う別々のグループを柔軟に作成したり、グループやユーザーに対して個別のロールを有効にしたりすることはできません。

![AOBO を使用したテナント管理](../media/csp-1.jpg)

## <a name="azure-delegated-resource-management"></a>Azure の委任されたリソース管理

Azure の委任されたリソース管理を使用すると、次の図に示すように、さまざまなグループをさまざまな顧客またはロールに割り当てることができます。 ユーザーは Azure の委任されたリソース管理によって適切なレベルのアクセス権を持つことになるため、管理エージェント ロールを持つ (つまり、完全な AOBO アクセス権を持つ) ユーザーの数を減らすことができます。 これにより、顧客のリソースへの不要なアクセスが制限されるので、セキュリティの強化につながります。 また、より柔軟に、複数の顧客を大規模に管理できます。

CSP プログラムを使用して作成したサブスクリプションをオンボードするには、[Azure の委任されたリソース管理へのサブスクリプションのオンボード](../how-to/onboard-customer.md)に関する記事で説明されている手順を参照してください。 テナント内に管理エージェント ロールを持つすべてのユーザーが、このオンボードを実行できます。

![AOBO と Azure の委任されたリソース管理を使用したテナント管理](../media/csp-2.jpg)

> [!NOTE]
> [Azure portal の **[マイ カスタマー]** ページ](../how-to/view-manage-customers.md)に、 **[クラウド ソリューション プロバイダー (プレビュー)]** セクションが含まれるようになり、[Microsoft 顧客契約 (MCA) に署名](https://docs.microsoft.com/partner-center/confirm-customer-agreement)し、[Azure プランに含まれている](https://docs.microsoft.com/partner-center/azure-plan-get-started) CSP のお客様の課金情報とリソースが表示されます。 詳しくは、「[Microsoft Partner Agreement の課金アカウントの概要](../../billing/mpa-overview.md)」をご覧ください。
>
> CSP のお客様は、Azure の委任されたリソース管理にもオンボードされているかどうかにかかわらず、このセクションに表示されることがあります。 オンボードされている場合は、「**顧客と委任されたリソースを表示し、管理する**」に説明されているように、[[顧客]](../how-to/view-manage-customers.md) セクションにも表示されます。 同様に、CSP のお客様は、Azure の委任されたリソース管理にオンボードされるために、 **[マイ カスタマー]** の **[クラウド ソリューション プロバイダー (プレビュー)]** セクションに表示される必要はありません。

## <a name="next-steps"></a>次のステップ

- [テナント間の管理エクスペリエンス](cross-tenant-management-experience.md)について学習します。
- [Azure の委任されたリソース管理にサブスクリプションをオンボード](../how-to/onboard-customer.md)する方法について説明します。
- [Cloud Solution Provider プログラム](https://docs.microsoft.com/partner-center/csp-overview)について学習します。
