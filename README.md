# BuildCored-Orcas-Day26
CacheSim — BUILDCORED ORCAS Day 26

What it does. This tool is a visual playground that shows how a CPU manages memory using a two-level cache (L1 and L2). It demonstrates how keeping frequently used data in small fast buckets nearby prevents the CPU from having to wait on the much slower main RAM.

Hardware concept. Modern CPUs use a cache hierarchy because fast memory is expensive and small while slow memory is cheap and large. By using temporal locality reusing the same data and spatial locality - using nearby data, the hardware tries to predict what you'll need next to minimize misses that stall the processor.

1. pattern_sequential: Accesses addresses in order (0, 1, 2...), testing spatial locality by seeing if the cache can keep up with a linear stream.
2. pattern_repeated: Hits the same few addresses over and over to prove temporal locality where the cache shines by never needing to fetch from RAM twice.
3. pattern_strided: Jumps across memory e.g. every 5th address which often confuses caches because the data is too far apart to be grouped together.
4. pattern_random: Accesses memory with no logic; this is a cache's worst nightmare because it makes it impossible to predict or reuse data effectively.
5. pattern_zero_l1_hits: Uses a loop of 5 unique addresses to outsmart the 4-slot L1 cache ensuring the next needed item was just evicted thrashing.
6. pattern_perfect_l1: Limits itself to only 4 unique addresses so that once the cache is warmed up every single request is found instantly in L1.

Screen recording. https://drive.google.com/file/d/1k1uR45KFsA8AVwJOQMGlYdGInjYWJvaG/view?usp=sharing

What I would do differently. I would implement set-associative mapping which limits where a specific piece of data can live in the cache rather than allowing it to go anywhere. I'd also add a write-back policy to simulate what happens when the CPU modifies data, which adds extra complexity to keeping the L1, L2, and RAM in sync.

Run it. python day26_starter.py
