---
title: 主キー、外部キー、および一意キー
description: Azure Synapse Analytics の SQL Analytics でのテーブル制約のサポート
services: synapse-analytics
author: XiaoyuMSFT
manager: craigg
ms.service: synapse-analytics
ms.topic: conceptual
ms.subservice: ''
ms.date: 09/05/2019
ms.author: xiaoyul
ms.reviewer: nibruno; jrasnick
ms.custom: seo-lt-2019, azure-synapse
ms.openlocfilehash: b9336a5e230e90e1abd7f2d40d431b988385c009
ms.sourcegitcommit: 8a9c54c82ab8f922be54fb2fcfd880815f25de77
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80350034"
---
# <a name="primary-key-foreign-key-and-unique-key-in-sql-analytics"></a>SQL Analytics の主キー、外部キー、および一意キー

主キー、外部キー、一意キーなど、SQL Analytics のテーブル制約について説明します。

## <a name="table-constraints"></a>テーブル制約 
SQL Analytics では、次のテーブル制約がサポートされています。 
- PRIMARY KEY は、NONCLUSTERED と NOT ENFORCED が両方とも使用されている場合にのみサポートされます。    
- UNIQUE 制約は、NOT ENFORCED が使用されている場合にのみサポートされます。   

FOREIGN KEY 制約は SQL Analytics ではサポートされません。  

## <a name="remarks"></a>解説
主キーまたは一意キー (あるいはその両方) を使用すると、SQL Analytics エンジンでクエリの最適な実行プランを生成できます。  主キー列または一意制約列のすべての値は、一意である必要があります。 

SQL Analytics で主キーまたは一意制約を使用してテーブルを作成した後、ユーザーはそれらの列のすべての値が一意であることを確認する必要があります。  これに違反すると、クエリで不正確な結果が返される可能性があります。  この例では、主キーまたは一意制約の列に重複した値が含まれている場合に、クエリでどのように不正確な結果が返される可能性があるかを示します。  

```sql
 -- Create table t1
CREATE TABLE t1 (a1 INT NOT NULL, b1 INT) WITH (DISTRIBUTION = ROUND_ROBIN)

-- Insert values to table t1 with duplicate values in column a1.
INSERT INTO t1 VALUES (1, 100)
INSERT INTO t1 VALUES (1, 1000)
INSERT INTO t1 VALUES (2, 200)
INSERT INTO t1 VALUES (3, 300)
INSERT INTO t1 VALUES (4, 400)

-- Run this query.  No primary key or unique constraint.  4 rows returned. Correct result.
SELECT a1, COUNT(*) AS total FROM t1 GROUP BY a1

/*
a1          total
----------- -----------
1           2
2           1
3           1
4           1

(4 rows affected)
*/

-- Add unique constraint
ALTER TABLE t1 ADD CONSTRAINT unique_t1_a1 unique (a1) NOT ENFORCED

-- Re-run this query.  5 rows returned.  Incorrect result.
SELECT a1, count(*) AS total FROM t1 GROUP BY a1

/*
a1          total
----------- -----------
2           1
4           1
1           1
3           1
1           1

(5 rows affected)
*/

-- Drop unique constraint.
ALTER TABLE t1 DROP CONSTRAINT unique_t1_a1

-- Add primary key constraint
ALTER TABLE t1 add CONSTRAINT PK_t1_a1 PRIMARY KEY NONCLUSTERED (a1) NOT ENFORCED

-- Re-run this query.  5 rows returned.  Incorrect result.
SELECT a1, COUNT(*) AS total FROM t1 GROUP BY a1

/*
a1          total
----------- -----------
2           1
4           1
1           1
3           1
1           1

(5 rows affected)
*/

-- Manually fix the duplicate values in a1
UPDATE t1 SET a1 = 0 WHERE b1 = 1000

-- Verify no duplicate values in column a1 
SELECT * FROM t1

/*
a1          b1
----------- -----------
2           200
3           300
4           400
0           1000
1           100

(5 rows affected)
*/

-- Add unique constraint
ALTER TABLE t1 add CONSTRAINT unique_t1_a1 UNIQUE (a1) NOT ENFORCED  

-- Re-run this query.  5 rows returned.  Correct result.
SELECT a1, COUNT(*) as total FROM t1 GROUP BY a1

/*
a1          total
----------- -----------
2           1
3           1
4           1
0           1
1           1

(5 rows affected)
*/

-- Drop unique constraint.
ALTER TABLE t1 DROP CONSTRAINT unique_t1_a1

-- Add primary key contraint
ALTER TABLE t1 ADD CONSTRAINT PK_t1_a1 PRIMARY KEY NONCLUSTERED (a1) NOT ENFORCED

-- Re-run this query.  5 rows returned.  Correct result.
SELECT a1, COUNT(*) AS total FROM t1 GROUP BY a1

/*
a1          total
----------- -----------
2           1
3           1
4           1
0           1
1           1

(5 rows affected)
*/

```

## <a name="examples"></a>例
主キーを設定して SQL Analytics テーブルを作成する 

```sql 
CREATE TABLE mytable (c1 INT PRIMARY KEY NONCLUSTERED NOT ENFORCED, c2 INT);
```
一意制約を設定して SQL Analytics テーブルを作成する

```sql
CREATE TABLE t6 (c1 INT UNIQUE NOT ENFORCED, c2 INT);
```

## <a name="next-steps"></a>次のステップ

SQL Analytics データベースにテーブルを作成したら、次の手順はテーブルへのデータの読み込みです。 読み込みのチュートリアルについては、[SQL Analytics データベースへのデータの読み込み](load-data-wideworldimportersdw.md)に関するページを参照してください。
