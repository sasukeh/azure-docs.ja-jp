---
title: 監査ログにアクセスする - Azure portal - Azure Database for MariaDB
description: この記事では、Azure portal から Azure Database for MariaDB の監査ログを構成し、それにアクセスする方法について説明します。
author: ajlam
ms.author: andrela
ms.service: mariadb
ms.topic: conceptual
ms.date: 3/18/2020
ms.openlocfilehash: d31b7531e00199ea63c7b057dacff1b67d7cedc6
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2020
ms.locfileid: "79528933"
---
# <a name="configure-and-access-audit-logs-in-the-azure-portal"></a>Azure portal での監査ログの構成とアクセス

[Azure Database for MariaDB の監査ログ](concepts-audit-logs.md)と診断設定を Azure portal から構成することができます。

> [!IMPORTANT]
> 監査ログ機能は現在、プレビュー段階です。

## <a name="prerequisites"></a>前提条件

このハウツー ガイドの手順を実行するには、以下が必要です。

- [Azure Database for MariaDB サーバー](quickstart-create-mariadb-server-database-using-azure-portal.md)

## <a name="configure-audit-logging"></a>監査ログを構成する

監査ログを有効化および構成します。

1. [Azure portal](https://portal.azure.com/) にサインインする

1. Azure Database for MariaDB サーバーを選択します。

1. サイドバーの **[設定]** セクションで、 **[サーバー パラメーター]** を選択します。
    ![サーバー パラメーター](./media/howto-configure-audit-logs-portal/server-parameters.png)

1. **audit_log_enabled** パラメーターを ON に更新します。
    ![監査ログの有効化](./media/howto-configure-audit-logs-portal/audit-log-enabled.png)

1. [audit_log_events](concepts-audit-logs.md#configure-audit-logging) パラメーターを更新して、ログに記録する**イベントの種類**を選択します。
    ![監査ログのイベント](./media/howto-configure-audit-logs-portal/audit-log-events.png)

1. **audit_log_exclude_users** パラメーターを更新して、ログから除外する MariaDB ユーザーを追加します。 ユーザーは MariaDB ユーザー名で指定します。
    ![監査ログの除外ユーザー](./media/howto-configure-audit-logs-portal/audit-log-exclude-users.png)

1. パラメーターを変更すると、 **[保存]** をクリックできます。 または変更を **[破棄]** することができます。
    ![および](./media/howto-configure-audit-logs-portal/save-parameters.png)

## <a name="set-up-diagnostic-logs"></a>診断ログの設定

1. サイドバーの **[監視]** セクションの下で、 **[診断設定]** を選択します。

1. [+ Add diagnostic setting] (診断設定の追加) をクリックします。![診断設定の追加](./media/howto-configure-audit-logs-portal/add-diagnostic-setting.png)

1. 診断設定の名前を指定します。

1. どのデータ シンク (ストレージ アカウント、イベント ハブ、Log Analytics ワークスペース) に監査ログを送信するか指定します。

1. ログの種類として "MySqlAuditLogs" を選択します。
![診断設定の構成](./media/howto-configure-audit-logs-portal/configure-diagnostic-setting.png)

1. 監査ログをパイプするようにデータ シンクを設定したら、 **[保存]** をクリックすることができます。
![診断設定の保存](./media/howto-configure-audit-logs-portal/save-diagnostic-setting.png)

1. 構成したデータ シンクを調べて監査ログにアクセスします。 ログが表示されるまでに最大で 10 分かかる可能性があります。

## <a name="next-steps"></a>次のステップ

- Azure Database for MariaDB の[監査ログ](concepts-audit-logs.md)の詳細について学習します。