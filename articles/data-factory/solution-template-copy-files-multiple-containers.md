---
title: 複数のコンテナーからのファイルのコピー
description: Azure Data Factory を使用して複数のコンテナーからファイルをコピーするための、ソリューション テンプレート の使用方法について説明します。
services: data-factory
author: dearandyxu
ms.author: yexu
ms.reviewer: douglasl
manager: anandsub
ms.service: data-factory
ms.workload: data-services
ms.topic: conceptual
ms.custom: seo-lt-2019
ms.date: 11/1/2018
ms.openlocfilehash: 0c4c26ba163f83483b3eb48e51d91f9a919a887c
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "75439841"
---
# <a name="copy-files-from-multiple-containers-with-azure-data-factory"></a>Azure Data Factory を使用して複数のコンテナーからファイルをコピーする

この記事では、ファイル ストア間で複数のコンテナーからファイルをコピーするために使用できる、ソリューション テンプレートについて説明します。 たとえば、AWS S3 から Azure Data Lake Store にデータ レイクを移行することもできます。 また、テンプレートを使用して、1 つの Azure BLOB ストレージ アカウントに含まれるすべてのファイルを、別の Azure Blob ストレージ アカウントにレプリケートすることもできます。

> [!NOTE]
> 1 つのコンテナーからファイルをコピーする場合は、[データのコピー ツール](copy-data-tool.md)を使用して、単一のコピー アクティビティを含んだパイプラインを作成する方が効率的です。 この記事に示すテンプレートは、そのシンプルなシナリオで必要とするものより大きくなっています。

## <a name="about-this-solution-template"></a>このソリューション テンプレートについて

このテンプレートでは、ソース ストレージ ストアからコンテナーを列挙します。 その後、それらのコンテナーをコピー先のストアにコピーします。

このテンプレートには、3 つのアクティビティが含まれています。
- **GetMetadata** は、ソース ストレージ ストアをスキャンし、コンテナーの一覧を取得します。
- **ForEach** は、**GetMetadata** アクティビティからコンテナーの一覧を取得し、その一覧を反復処理して、各コンテナーを Copy アクティビティに渡します。
- **Copy** は、各コンテナーをソース ストレージ ストアからコピー先ストアにコピーします。

このテンプレートでは、次のパラメーターを定義します。
- *SourceFileFolder* は、コンテナーの一覧を取得できるデータ ソース ストアのフォルダー パスです。 このパスは複数のコンテナー フォルダーを格納するルート ディレクトリです。 このパラメーターの既定値は `sourcefolder` です。
- *SourceFileDirectory* は、データ ソース ストアのルート ディレクトリの下にあるサブフォルダーのパスです。 このパラメーターの既定値は `subfolder` です。
- *DestinationFileFolder* は、コピー先ストア内でファイルがコピーされる場所のフォルダー パスです。 このパラメーターの既定値は `destinationfolder` です。
- *DestinationFileDirectory* は、コピー先ストア内でファイルがコピーされる場所のサブフォルダー パスです。 このパラメーターの既定値は `subfolder` です。

## <a name="how-to-use-this-solution-template"></a>このソリューション テンプレートの使用方法

1. **Copy multiple files containers between File Stores** テンプレートに移動します。 ソース ストレージ ストアへの **[新規]** 接続を作成します。 ソース ストレージ ストアは、複数のコンテナーからファイルをコピーする場所 (コピー元) です。

    ![ソースへの新しい接続を作成する](media/solution-template-copy-files-multiple-containers/copy-files-multiple-containers-image1.png)

2. コピー先ストレージ ストアへの **[新規]** 接続を作成します。

    ![コピー先への新しい接続を作成する](media/solution-template-copy-files-multiple-containers/copy-files-multiple-containers-image2.png)

3. **[このテンプレートを使用]** を選択します。

    ![このテンプレートを使用](media/solution-template-copy-files-multiple-containers/copy-files-multiple-containers-image3.png)
    
4. 次の例に示すように、パイプラインが表示されます。

    ![パイプラインを表示する](media/solution-template-copy-files-multiple-containers/copy-files-multiple-containers-image4.png)

5. **[デバッグ]** を選択し、 **[パラメーター]** で入力し、 **[完了]** を選択します。

    ![パイプラインを実行する](media/solution-template-copy-files-multiple-containers/copy-files-multiple-containers-image5.png)

6. 結果を確認します。

    ![結果を確認する](media/solution-template-copy-files-multiple-containers/copy-files-multiple-containers-image6.png)

## <a name="next-steps"></a>次のステップ

- [Azure Data Factory で制御テーブルを使用してデータベースから一括コピーを行う](solution-template-bulk-copy-with-control-table.md)

- [Azure Data Factory を使用して複数のコンテナーからファイルをコピーする](solution-template-copy-files-multiple-containers.md)
