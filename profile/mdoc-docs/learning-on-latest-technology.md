### Learning on latest technology


#### database survey
- aws redshift is slow for OLAP purpose db
    - over 180 millions rows of data
    - 3 milliions rows/month
    - critical as redshift stalled => ex: impact reporting service
- we consider migrate redshift to self owned database
- benefit: save cost to 1/3 in the similar hardware spec
- estimate migrate effort


#### database options
- [postgresql](https://www.postgresql.org/)<!-- .element: target="_blank" -->
- [clickhouse](https://clickhouse.tech/)<!-- .element: target="_blank" -->


#### simple compare(1)
|metrics |redshift |postgres v13.6 |clickhouse v21.2|
|----------------|-------------------------------|-----------------------------|-----------------------------|
|OLAP or OLTP |OLAP |OLTP |OLAP|
|CAP |don't care |AC => CP on replica |AP on replica|
|table constraint |sort, dist keys method |indexing |indexing|
|data types |fewer data type support |more data types support |more data types(include protobuf, parquet)|
|scalability |easy by setting |maintain by our self |maintain by our self|
|cost |estimate 3000rmb/month |1000rmb/month |1000rmb/month|
<!-- .element: style="position: absolute;  left: 0; box-shadow: 0 1px 4px; padding: 20px; font-size: 30px; text-align: left;" -->


#### simple compare(2)
|metrics |redshift |postgres v13.6 |clickhouse v21.2|
|----------------|-------------------------------|-----------------------------|-----------------------------|
|SQL syntax |standard |standard |standard after 19.9.1|
|pros |- don't need to maintain server |- more flexible for data type |- more flexible for data type|
||- easy for scalability |- more flexible for plugins |- performance much better than postgresql|
||- can use COPY feature in s3 |- |- can pretend as postgress|
||- |- |- support aws s3 import/export|
<!-- .element: style="position: absolute;  left: 0; box-shadow: 0 1px 4px; padding: 20px; font-size: 30px; text-align: left;" -->


#### simple compare(3)
|metrics |redshift |postgres v13.6 |clickhouse v21.2|
|----------------|-------------------------------|-----------------------------|-----------------------------|
|cons |- slow on query in current context |- need to handle server failure |- usage need to handle server failure|
||- higher cost |- need to handle s3 import/export |- no acutual update/delete|
|||- performance may be slower than Redshift due to sql ||
<!-- .element: style="position: absolute;  left: 0; box-shadow: 0 1px 4px; padding: 20px; font-size: 30px; text-align: left;" -->


#### POC of performance: postgres vs clickhouse
- 3 million rows of data(one month)
- import to postgres and clickhouse
- simple query and compare
```
select count(*) from warehouse;
```
|metrics |postgres v13.6 |clickhouse v21.2|
|----------------|-----------------------------|-----------------------------|
|count |3,373,910| 3,440,309|
|time|936.062 ms|4ms|