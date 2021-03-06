---
title: Azure Data Lake Storage Gen2 に関する既知の問題 | Microsoft Docs
description: Azure Data Lake Storage Gen2 に関する制限と既知の問題について説明します。
author: normesta
ms.subservice: data-lake-storage-gen2
ms.service: storage
ms.topic: conceptual
ms.date: 03/20/2020
ms.author: normesta
ms.reviewer: jamesbak
ms.openlocfilehash: 4f8fae6580272ed53b8d440ba3e74c6a1ed1e61a
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2020
ms.locfileid: "80061509"
---
# <a name="known-issues-with-azure-data-lake-storage-gen2"></a>Azure Data Lake Storage Gen2 に関する既知の問題

この記事では、Azure Data Lake Storage Gen2 に関する制限と既知の問題について説明します。

## <a name="supported-blob-storage-features"></a>サポートされる BLOB ストレージの機能

階層型名前空間を持つアカウントで、より多くの BLOB ストレージ機能が動作するようになりました。 完全な一覧については、「[Azure Data Lake Storage Gen2 で使用できる BLOB ストレージ機能](data-lake-storage-supported-blob-storage-features.md)」を参照してください。

## <a name="supported-azure-service-integrations"></a>サポートされる Azure サービスの統合

Data Lake Storage gen2 は、データの取り込み、分析の実行、およびビジュアル表現の作成に使用できるいくつかの Azure サービスをサポートしています。 サポートされる Azure サービスの一覧については、「[Azure Data Lake Storage Gen2 をサポートする Azure サービス](data-lake-storage-supported-azure-services.md)」を参照してください。

「[Azure Data Lake Storage Gen2 をサポートするAzure サービス](data-lake-storage-supported-azure-services.md)」を参照してください。

## <a name="supported-open-source-platforms"></a>サポートされるオープン ソース プラットフォーム

一部のオープン ソース プラットフォームは Data Lake Storage Gen2 をサポートしています。 完全な一覧については、「[Data Lake Storage Gen2 をサポートするオープン ソース プラットフォーム](data-lake-storage-supported-open-source-platforms.md)」を参照してください。

「[Azure Data Lake Storage Gen2 をサポートするオープン ソース プラットフォーム](data-lake-storage-supported-open-source-platforms.md)」を参照してください。

## <a name="blob-storage-apis"></a>BLOB ストレージ API

BLOB API と Data Lake Storage Gen2 API では、同じデータを処理できます。

このセクションでは、BLOB API と Data Lake Storage Gen2 API を使用して同じデータを操作する場合の問題と制限事項について説明します。

* BLOB API と Data Lake Storage API の両方を使用して、ファイルの同じインスタンスに書き込むことはできません。 Data Lake Storage Gen2 API を使用してファイルに書き込むと、そのファイルのブロックは、[Get Block List](https://docs.microsoft.com/rest/api/storageservices/get-block-list) BLOB API への呼び出しで認識されなくなります。 Data Lake Storage Gen2 API または BLOB API のいずれかを使用して、ファイルを上書きできます。 これはファイルのプロパティには影響しません。

* 区切り記号を指定せずに [List Blobs](https://docs.microsoft.com/rest/api/storageservices/list-blobs) 操作を使用した場合、結果にはディレクトリと BLOB の両方が含まれます。 区切り記号を使用する場合は、スラッシュ (`/`) のみを使用してください。 サポートされている区切り記号はこれだけです。

* [Delete Blob](https://docs.microsoft.com/rest/api/storageservices/delete-blob) API を使用してディレクトリを削除した場合、そのディレクトリは空の場合にのみ削除されます。 これは、Blob API を使用してディレクトリを再帰的に削除することはできないことを意味します。

次の BLOB REST API はサポートされていません。

* [Put Blob (Page)](https://docs.microsoft.com/rest/api/storageservices/put-blob)
* [Put Page](https://docs.microsoft.com/rest/api/storageservices/put-page)
* [Get Page Ranges](https://docs.microsoft.com/rest/api/storageservices/get-page-ranges)
* [Incremental Copy Blob](https://docs.microsoft.com/rest/api/storageservices/incremental-copy-blob)
* [Put Page from URL](https://docs.microsoft.com/rest/api/storageservices/put-page-from-url)
* [Put Blob (Append)](https://docs.microsoft.com/rest/api/storageservices/put-blob)
* [Append Block](https://docs.microsoft.com/rest/api/storageservices/append-block)
* [Append Block from URL](https://docs.microsoft.com/rest/api/storageservices/append-block-from-url)

アンマネージド VM ディスクは、階層型名前空間があるアカウントではサポートされていません。 ストレージ アカウントで階層型名前空間を有効にする場合は、階層型名前空間機能が有効ではないストレージ アカウントにアンマネージド VM ディスクを配置してください。

<a id="api-scope-data-lake-client-library" />

## <a name="file-system-support-in-sdks"></a>SDK でのファイル システムのサポート

get および set ACL 操作は現在、再帰的ではありません。

## <a name="file-system-support-in-powershell-and-azure-cli"></a>PowerShell と Azure CLI でのファイル システムのサポート

- [PowerShell](data-lake-storage-directory-file-acl-powershell.md) と [Azure CLI](data-lake-storage-directory-file-acl-cli.md) のサポートは、パブリック プレビュー段階です。
- get および set ACL 操作は現在、再帰的ではありません。

## <a name="lifecycle-management-policies"></a>ライフサイクル管理ポリシー

* BLOB スナップショットの削除は、まだサポートされていません。  

## <a name="archive-tier"></a>アーカイブ層

現在、アーカイブ アクセス層に影響するバグがあります。


## <a name="blobfuse"></a>blobfuse

Blobfuse はサポートされていません。

<a id="known-issues-tools" />

## <a name="azcopy"></a>AzCopy

AzCopy の最新バージョン ([AzCopy v10](https://docs.microsoft.com/azure/storage/common/storage-use-azcopy-v10?toc=%2fazure%2fstorage%2ftables%2ftoc.json)) のみを使用してください。 AzCopy の以前のバージョン (AzCopy v8.1 など) はサポートされていません。

<a id="storage-explorer" />

## <a name="azure-storage-explorer"></a>Azure ストレージ エクスプローラー

バージョン  `1.6.0` 以降のみを使用します。

<a id="explorer-in-portal" />

## <a name="storage-explorer-in-the-azure-portal"></a>Azure portal での Storage Explorer

ACL はまだサポートされていません。

<a id="third-party-apps" />

## <a name="thirdpartyapplications"></a>サード パーティ製アプリケーション

REST API を使用して動作するサード パーティ製アプリケーションは、Blob API を呼び出す Data Lake Storage Gen2 アプリケーションと一緒に使用すると、そのアプリケーションが動作するのと同じように引き続き動作します。

## <a name="access-control-lists-acl-and-anonymous-read-access"></a>アクセス制御リスト (ACL) と匿名読み取りアクセス

コンテナーへの[匿名読み取りアクセス](storage-manage-access-to-resources.md)が許可されている場合、そのコンテナーやコンテナーに含まれているファイルには ACL は作用しません。

## <a name="windows-azure-storage-blob-wasb-driver"></a>Windows Azure Storage Blob (WASB) ドライバー

現在、階層型名前空間があるアカウントと共に、WASB ドライバーの使用に関して、いくつかの問題があります。 ワークロードには、[Azure Blob File System (ABFS)](data-lake-storage-abfs-driver.md) ドライバーを使用することをお勧めします。 





