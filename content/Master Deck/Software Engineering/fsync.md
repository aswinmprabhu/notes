fsync()  
  
**Flushes dirtied pages to disk. This includes writing through disk caches.**  
fdatasync() - Only sync data and not metadata.  
  
Mongo flushes every 100ms.  
Only all writes from last fsync are flushed (not last SUCCESSFUL fsync) -- hence, postgres crashes on fsync failures.

---
