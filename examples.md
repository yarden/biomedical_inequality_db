Example queries to NIH Biomedical Inequality database
========================================

Querying funding table
--------------------------

* Calculate total number of grants awarded to Johns Hopkins University in 1985:

```
sqlite> SELECT ORG_NAME, COUNT(DISTINCT application_id) FROM funding_table WHERE org_id='1910777' AND FY="1985";
JOHNS HOPKINS UNIVERSITY|1108
```

* Tabulate number of grants awarded to the institute by type in 1985

Querying publications table
--------------------------

* Tabulate number of publications associated with R01 grants by year from 1985-1990: 

```
sqlite> SELECT FY, COUNT(DISTINCT pmid) FROM pubs_table WHERE FY >= 1985 AND FY <= 1990 GROUP BY FY;
1985|22737
1986|19560
1987|21521
1988|24149
1989|25900
1990|26710
```

* Get number of publications produced by Stanford University from 2010-2015:

```
sqlite> SELECT FY, COUNT(DISTINCT pmid) FROM pubs_table WHERE FY >= 2010 AND org_id='9214214' GROUP BY FY;
2010|1136
2011|1170
2012|1082
2013|1217
2014|1247
2015|1240
```

* Get total number of citations Stanford University had in 2010:

```
sqlite> SELECT SUM(num_cites) FROM (SELECT DISTINCT pmid, num_cites FROM pubs_table WHERE FY=2010 AND org_id='9214214');
```

Querying the patents table
------------------------

* Get top five organizations with largest number of patents:

```
sqlite> SELECT COUNT(DISTINCT patent_id), PATENT_ORG_NAME FROM patents_table GROUP BY PATENT_ORG_NAME ORDER BY COUNT(DISTINCT patent_id) DESC LIMIT 5;
960|STANFORD UNIVERSITY
945|UNIVERSITY OF WISCONSIN-MADISON
640|SCRIPPS RESEARCH INSTITUTE
639|UNIVERSITY OF CALIFORNIA SYS OFFICE/PRES
549|MASSACHUSETTS INSTITUTE OF TECHNOLOGY
```
