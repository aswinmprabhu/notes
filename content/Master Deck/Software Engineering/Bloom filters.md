Bloom filters  
  
**Probabilistic** set data structure.  
False = Definitely not there.  
True = Maybe there.  
Space complexity = **O(log n)**  
  
Works with **bitmaps**.   
Keys => Hash functions => Mod output by bitmap size => Set bitmap bits.

---
