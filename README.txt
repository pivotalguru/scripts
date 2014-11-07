README file for Scripts
*******************************************************************************************************
Site: http://www.PivotalGuru.com
Author: Jon Roberts
Email: jgronline@gmail.com
Date: 2014-11-07
*******************************************************************************************************

Scripts for maintaining Greenplum Database and HAWQ.

1.  maintain.sh

HAWQ and GPDB
- VACUUM ANALYZE all tables in pg_catalog

GPDB Only
- REINDEX the system catalog (reindexdb -s)
- ANALYZE tables with missing statistics (gp_toolkit.gp_stats_missing).  A partitioned table always shows up here so I ignore those and check for partitions/inherited tables with missing statistics.
- VACUUM heap tables near the transaction wraparound point
- VACUUM heap tables with bloat (gp_toolkit.gp_bloat_diag)
- VACUUM AO tables with bloat (gp_toolkit.__gp_aovisimap_hidden_info). I'm using 5% as the threshold.