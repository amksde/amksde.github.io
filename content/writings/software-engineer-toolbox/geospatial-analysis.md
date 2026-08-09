---
title : "Geospatial Query & Analysis"
---

When we need to query upon latitude and longitude of items in our database, simple 2-dimensional scans are not efficient.

Most popular algorithms on which real-world implementations are based are:
1. [GeoHash](https://en.wikipedia.org/wiki/Geohash)
   - Divide regions into smaller regions
   - hash length will define the precision of the box
   - can be stored in **DB**
2. [QuadTree](https://en.wikipedia.org/wiki/Quadtree)
   - Create an in memory tree
   - For around 200M data points, a tree can be created that fits into 1G of memory
   - Updates need to backed up since they will be lost on server startup
3. [Google S2](https://s2geometry.io/)
4. [R-Tree](https://en.wikipedia.org/wiki/R-tree)
   - Used in PostGis

All popular databases support geospatial analysis
- [MongoDB](https://www.mongodb.com/docs/manual/geospatial-queries/)
- [ElasticSearch](https://www.elastic.co/docs/explore-analyze/geospatial-analysis)
- [Postgres](https://postgis.net/)
  - Uses R-Trees
- [Redis](https://redis.io/docs/latest/develop/ai/search-and-query/query/geo-spatial/)
