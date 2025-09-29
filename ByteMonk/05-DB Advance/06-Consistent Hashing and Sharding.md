# **System Design: Database Sharding & Consistent Hashing - Short Notes**

## **1. What is Sharding?**
- **Horizontal partitioning** of database tables by **splitting rows across multiple machines** (shards)
- Each shard can be:
  - A separate disk partition
  - A different disk
  - A completely separate machine
- **Goal:** Scale databases to handle growing data/traffic

## **2. Sharding Architecture Components**
| Component | Purpose |
|-----------|---------|
| **Router** | Routes read/write requests to correct shard |
| **Config Server** | Stores sharding algorithm and mapping logic |

## **3. Key Requirements for Effective Sharding**
1. **Even Data Distribution**
   - Avoid "hot shards" (millions reqs to Shard1 vs 1 req to Shard2)
2. **Minimal Impact During Changes**
   - Adding/removing shards shouldn't disrupt system
3. **Failure Resilience**
   - Single shard failure shouldn't crash system

## **4. Sharding Algorithms**

### **A. Simple Hashing (Problematic)**
```python
shard = hash(user_id) % number_of_shards
```
❌ **Problems:**
- Adding/removing shards requires **complete data redistribution**
- Extremely expensive operation

### **B. Consistent Hashing (Improved Solution)**
4. **Concept:**
   - Uses a **hash ring** (circular number space)
   - Both servers and data keys are mapped to the ring

5. **How It Works:**
   - Each shard gets multiple positions on ring (via hashing)
   - Data keys fall into nearest shard's segment

6. **Advantages:**
   - Adding/removing shards only affects **adjacent segments**
   - No need for full data redistribution

7. **Replication for Fault Tolerance:**
   - Each shard's data is replicated to next shard(s) on ring
   - If Shard3 fails, Shard4 takes over its segment

## **5. Operational Benefits**
✅ **Adding Shards:**
8. Pre-seed data via replication from adjacent shards
9. Bring new shard online with minimal impact

✅ **Removing/Failed Shards:**
- Replica shards automatically handle requests
- No immediate data redistribution needed

## **6. Visual Comparison**

**Simple Hashing**  
User1 → Hash → Mod N → ShardX  
*Changing N requires all data to move*

**Consistent Hashing**  
``` 
Hash Ring:
[Shard1]----[UserA]----[Shard2]----[UserB]----[Shard3]
```
*Only adjacent segments affected by changes*

## **7. Key Takeaways**
✔ Sharding enables **horizontal scaling** of databases  
✔ **Consistent hashing** > simple hashing for dynamic systems  
✔ Replication provides **fault tolerance**  
✔ Config servers enable **transparent routing**  
