# SAP HANA
## SAP HANA Platform
### Processing Service
#### Application Pushdown
- 
  In Memory, not only database but also Appplication.
  
  Calcutanion Logic is on HANA, and not to translate big data to application tier by network to calculate greate data to make small result.

### Appication Service
### Integration Services
### Database Services
- In Memory Database
  - HW
    - 
  - SW
    - 1. Raw and Column Store
      - One data image that is used of column store.
    - 2. Compression
      - Compressed to be able to read not to be uncompressed. 
    - 3. Partitoning
    - 4. Information View
    - 5. Optimization
      - Delta Merge, etc.

- Memory Assign
  - Code and stack
    - Binary Code
  - Tables
    - System Table
    - You should have about half of all emory
  - Workspace
    - 
  - Pool
  - License
    64GB / Unit

- Disk
  Used Like Backup.
  1. automatic backup to data volume by 5 minutes.
  2. changes to log volumes, when database committed. syncronizedly.

- Compress

### Structure
- Store
  - Main Store
    - optimized to select.
  - Delta Store
    - optimized to insert.
      
- Consistant View Manager
  - Give both of Delta Store and Main Store.

- Delta Merge
  

- Specification
  - Insert Only
    

### 階層的ata Storage System
- Dynamic Tearing
  - Hot Data
    In Memory
  - Warm Data
    - Disk Table
  - Cold Data
    - Hadoop, Outer Database

### Multi-tenant DataBase Container
- 
  Multi Database on one HANA Instance.
  
### 
- System Replication
  
### Scaleout Structure
- 
  Standby 
  

#### Memo
- Intel G4 Processor

## SAP HANA Vora
- 
  small software.
  required Hadoop, Spark.
  
  HANA 

## Link
- https://en.wikipedia.org/wiki/SAP_HANA
