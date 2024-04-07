---
layout: home
title: About
permalink: /
---

<img src="assets/schemapile.png" height="auto" width="400">


Access to fine-grained schema information is crucial for understanding how relational databases are designed and used in practice, and for building systems that help users interact with them. Furthermore, such information is required as training data to leverage the potential of large language models (LLMs) for improving data preparation, data integration and natural language querying. Existing single-table corpora such as GitTables provide insights into how tables are structured in-the-wild, but lack detailed schema information about how tables relate to each other, as well as metadata like data types or integrity constraints. On the other hand, existing multi-table (or database schema) datasets are rather small and attribute-poor, leaving it unclear to what extent they actually represent typical real-world database schemas.

In order to address these challenges, we present SchemaPile, a corpus of 221,171 database schemas, extracted from SQL files on GitHub. It contains 1.7 million tables with 10 million column definitions, 700 thousand foreign key relationships, seven million integrity constraints, and data content for more than 340 thousand tables. We conduct an in-depth analysis on the millions of schema metadata properties in our corpus, as well as its highly diverse language and topic distribution. In addition, we showcase the potential of SchemaPile to improve a variety of data management applications, e.g., fine-tuning LLMs for schema-only foreign key detection, improving CSV header detection and evaluating multi-dialect SQL parsers. We publish the code and data for recreating SchemaPile and a permissively licensed subset SchemaPile-Perm.

💾 Dataset: [SchemaPile (Zenodo)](https://zenodo.org/records/10931803).
🤗 Foreign Key Detection Models: [t5-schemapile-fk (HuggingFace)](https://huggingface.co/tdoehmen/t5-schemapile-fk), [starcoder-schemapile-fk (HuggingFace)](https://huggingface.co/tdoehmen/starcoder-schemapile-fk)
📄 Code: [Github Repo](https://github.com/amsterdata/schemapile/)

Please consider reporting cases of personal or otherwise undesired tables in SchemaPile to the email below. Feedback, suggestions and results from projects with SchemaPile are also very welcome!

t . r . doehmen @ uva.nl .