---
title: "Top 10 mistakes to avoid when using Hive/Impala on Hadoop"
date: 2021-06-23T17:04:26Z
tags: [hadoop, hive, impala]
categories: [data engineering, data science]
draft: false
---

I recently took a deep dive into Hadoop for a project where I needed to automate the population of tables using JSONs and CSVs. Inevitably, I made some mistakes along the way and would like to share the lessons learned. By sharing them, I hope to save you some time! Here are 10 mistakes to avoid making when using Hive and/or Impala:

  1. **You must invalidate metadata in Impala, if you are working with tables in Hive & Impala.** Hive and Impala work from the same data i.e. tables in Hadoop Distributed File System (HDFS), metadata in the Metastore. Impala caches the metadata of tables such that updates like drops or changing the structure of a table doesn’t get picked up automatically, so you must execute the invalidate metadata command. You can call invalidate metadata table; or invalidate metadata; to update for all tables if you have appropriate privileges. This command doesn’t work in Hive so only use Impala or call an Impala query from bash. Although Hive and Impala live on the same Hadoop cluster, the metadata for tables created using Hive does not get automatically updated on the Impala side. 
  2. **Create views for external products to use instead of tables as best practice.** Views can simplify complex logic or joins over multiple tables. They show the underlying logic of the query so are great for supporting legacy code. Views are also more secure as they permit the surfacing of selected columns and hiding of others from the user. 
  3. **Must flatten arrays and structs before creating views for dashboards.** Some dashboards only accept primitive data types in tables e.g. string and int and do not accept complex or user defined ones like arrays of structs.
  4. **To flatten arrays/structs in a column-wide manner, use Impala as it lends itself more easily to this.** You could use Hive with concat_ws or posexplode depending on the nature of your data i.e. how nested and type. Impala uses the dot notation to easily access nested data types like array<struct >. 
  5. **When flattening complex data types in Impala, use left outer joins to ensure that such columns aren’t removed while flattening them.** I spent way too much time debugging why whole rows were removed from my table because of empty arrays ([]) in a single column. 🤦🏾‍♀️
  6. **Use partitions only when the table will be searched regularly by this field.** Don’t overdo it! Partitions are directories on HDFS. Use buckets when you have a finite number of categories like states in the US.
  7. **All tables with complex data types must be stored as parquet to successfully extract or flatten in Impala.** It can be tricky to create parquet tables in Impala so do it in Hive first and don’t forget to invalidate in order to actually be able see the change to the table. 
  8. **Always check the structure of your JSONs before feeding them into HDFS.** I got the following error: “Error while processing statement: FAILED: Execution Error, return code 2 from org.apache.hadoop.hive.ql.exec.mr.MapRedTask (state=08S01,code=2)”. This obscure error meant that the JSON must start with {. I used an API that didn’t return all responses as strict JSONs, so I had to reformat all responses and check that all were wrapped in curly braces. 
  9. **Dynamic partitioning is a godsend when creating external tables based on JSONs or CSVs.** This avoids the need for manual parsing of the data file while reading files into Hive. It will locate the field that you wish to partition based on the schema specified. Magic!
  10. **Add metadata fields like timeLastModified or scriptname to your tables.** This enables your data files and their content to be tracked or logged after it populates a Hive table. You should also consider adding comments to tables describing source queries and fields in the table. 

Sources: [https://www.simplilearn.com/working-with-hive-and-impala-tutorial](<https://www.simplilearn.com/working-with-hive-and-impala-tutorial>)
