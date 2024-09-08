Isolation levels in a database  

- **Serializable** - **The highest isolation level. Reads always return data that is committed, including range based writes on multiple rows (avoiding phantom reads).**
- **MVCC** - **In MVCC when data is mutated, instead of locking + overwriting it, you create a new version of the data that new requests read from.**
- **Repeatable reads** - **Phantom reads are acceptable. (Multi-row cases)**
- **Read committed** - **Non-repeatable reads are acceptable.**
- **Read uncommitted** - **The lowest isolation level. Dirty reads are acceptable.**

---
