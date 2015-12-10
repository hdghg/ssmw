# Server-side migration wizard for openshift

This script solves problem of DB migration over some directed graph of versions
where each version is a verticle, and each migration script is a edge between
verticles. So it builds directed graph from providen migration and creation
scripts (for the case when you don't have DB scheme at all), then it finds all
possible migration paths between current version and required, and
tries these migration pathes in order from shortest path to longest. It joins
all migration scripts in speicific migration path into one temporary *.sql file,
which then it tries to execute in single transaction, if some error occured - it
will try to do same thing for all possible paths that it haven't tried yet.

Read detailed description of this script in ssmw.py