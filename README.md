# Spark-Echo

- Learning spark and it fascinates me to see how everything that is created boils down to some code. Trying to follow the footstep towards making a cheap copy of the legacy, just for the learning experience. 😄🎊
- I am actually keeping this in sync with whatever I am learning in the book. __"Spark : The definitive Guide"__

## What Spark problem I re-derived

## What I intentionally did NOT build

## Architecture diagram

## Execution flow walkthrough

## Example job with logs

## Learnings mapped to Spark internals

## Project Structure

```
minispark/
 ├── core/
 │   ├── rdd/
 │   │   ├── RDD.java
 │   │   ├── Partition.java
 │   │   ├── Dependency.java
 │   │   └── Lineage.java
 │   ├── scheduler/
 │   │   ├── DAG.java
 │   │   ├── Stage.java
 │   │   └── Scheduler.java
 │   ├── executor/
 │   │   ├── Task.java
 │   │   └── TaskRunner.java
 │   └── shuffle/
 │       ├── ShuffleWriter.java
 │       └── ShuffleReader.java
 ├── examples/
 ├── README.md
 └── docs/
```

### Phase 1 — Chapters: 1–3

- What all is covered in the chapters: 
  - What is Spark
  - Spark’s basic architecture
  - Driver / Executor model

- Your implementation
  - `SparkEchoContext`
  - Local “driver”
  - Fixed thread pool = executors

### Phase 2 — Chapters: 4–6

- What all is covered in the chapters: 
  - RDD abstraction
  - Transformations vs Actions
  - Laziness

- Implementation
  - `RDD<T>`
  - `map`, `filter`, `flatMap`
  - `collect`, `count`

### Phase 3 — Chapters: 7–8

- What all is covered in the chapters: 
  - Partitions
  - Parallel execution

- Implementation
  - Each RDD has `List<Partition>`
  - Partition = slice of data
  - Tasks = (RDD, partition)

### Phase 4 — Chapters: 9–10

- What all is covered in the chapters: 
  - groupBy, reduceByKey
  - Wide vs narrow transformations
  - Shuffle boundaries

- Implementation
  - `reduceByKey`
  - Detect wide dependency
  - Break DAG into stages
  - Write shuffle output to disk (or memory map)

 ### Phase 5 — Chapters: 11–12

- What all is covered in the chapters: 
  - Caching
  - Fault tolerance
  - Lineage graph

- Implementation
  - `cache()` flag on RDD
  - Lineage DAG
  - Kill a task → recompute from parents
 
### Phase 6 — Chapters: 13–15

- What all is covered in the chapters: 
  - Task retries
  - Simple scheduling policies

- Implementation
  - Retry failed task
  - Log stage/task execution
  - Simple FIFO scheduler
 
### Phase 7 — Chapters: 16–18

- What all is covered in the chapters: 
  - groupBy, reduceByKey
  - Wide vs narrow transformations
  - Shuffle boundaries

- Implementation
  - `reduceByKey`
  - Detect wide dependency
  - Break DAG into stages
  - Write shuffle output to disk (or memory map)
 
### Phase 8 — Chapters: 19+

- What all is covered in the chapters: 
  - Streaming = continuous micro-batch
  - Each batch = normal Spark job
  - Same DAG, same scheduler, repeated over time
  - Fault tolerance via replay + lineage

- Implementation
  - `StreamingContext`
  - DStream abstraction
  - Supported operations
    - map
    - filter
    - reduceByKey
    - window(windowSize, slideInterval)
    - foreachBatch(RDD -> action)



