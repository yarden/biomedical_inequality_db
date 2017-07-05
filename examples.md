Example queries to database of NIH Biomedical Inequality
========================================

* Tabulate number of publications associated with R01 grants by year: ::

  sqlite> SELECT FY, COUNT(DISTINCT pmid) FROM pubs_table GROUP BY FY;
  1985|22737
  1986|19560
  1987|21521
  1988|24149
  1989|25900
  1990|26710
  1991|27827
  1992|28248
  1993|28241
  1994|29313
  1995|28537
  1996|27572
  1997|30817
  1998|32357
  1999|35148
  2000|36415
  2001|37331
  2002|39242
  2003|39098
  2004|43374
  2005|46197
  2006|48808
  2007|51748
  2008|57024
  2009|62477
  2010|65538
  2011|65834
  2012|66518
  2013|67524
  2014|65342
  2015|63813
