---
layout: home
title: About
permalink: /
---

SchemaPile is a collection of database schemas, extracted from DDL/DML statements in SQL files on public code repositories.

<img src="assets/schemapile_format_wide.png" height="auto" width="400">

## Summary statistics

| Dataset                   | SchemaPile | SchemaPile-Perm |
|---------------------------|-----------:|----------------:|
| #Schemas                  |    221,171 |          22,989 |
| #Tables                   |       1.7M |            199K |
| #Schemas with data        |      75.6K |            7.1K |
| #Tables with data         |     347.0K |           34.9K |
| #Columns with data        |       2.2M |          219.0K |
| #Total data values        |      58.2M |            5.9M |
| Median #tables per schema |          4 |               4 |
| Mean #columns per schema  |        6.5 |             6.7 |
| Mean #values per column   |       27.6 |            28.7 |

## Usage Example

```shell
-- Download from Zenodo
curl -O https://zenodo.org/records/10931803/files/schemapile-perm.json.gz
```

```python
import gzip
import json
from collections import Counter

# Read file
with gzip.open("schemapile-perm.json.gz", 'r') as f:
    schemapile = json.loads(f.read())

# Look at example schema
print(schemapile['015036_schema.sql'])

# {'INFO': {'URL': 'https://github.com/nages103/k8s-petclinic/blob/bb75e895591...
# 'LICENSE': 'APACHE-2.0',
# 'PERMISSIVE': True},
# 'TABLES': {'vets': {'COLUMNS': {'id': {'TYPE': 'UnsignedInt',
#                                       'NULLABLE': False,
#                                       'UNIQUE': True,
#                                       'DEFAULT': None,
#                                       'CHECKS': [],
#  ...

# Get the 5 most common column names
column_names = []
for schema in schemapile:
    for table in schemapile[schema]["TABLES"]:
        for column_name in schemapile[schema]["TABLES"][table]["COLUMNS"]:
            column_names.append(column_name.lower())
column_names_schemapile = Counter(column_names)

print(column_names_schemapile.most_common(5))

# [('id', 84487),
# ('name', 28426),
# ('description', 14324),
# ('created_at', 12624),
# ('user_id', 10718)]
```

## Links

💾 Dataset: [SchemaPile (Zenodo)](https://zenodo.org/records/10931803)

🤗 Foreign Key Detection Models: 

- [t5-schemapile-fk (HuggingFace)](https://huggingface.co/tdoehmen/t5-schemapile-fk)
- [starcoder-schemapile-fk (HuggingFace)](https://huggingface.co/tdoehmen/starcoder-schemapile-fk)

📄 Code: [Github Repo](https://github.com/amsterdata/schemapile/)

Please consider reporting cases of personal or otherwise undesired tables in SchemaPile to the email below. Feedback, suggestions and results from projects with SchemaPile are also very welcome!

t . r . doehmen @ uva.nl .
