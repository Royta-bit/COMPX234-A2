# Readers-Writers Problem 

**Name:** He Chengxiang
**ID:** 20243006974

---

## Short design explanation

This project implements a **monitor-style solution** to the classic **Readers-Writers problem** using Python's `threading.Condition` primitive. The program simulates multiple reader and writer threads accessing a shared resource while enforcing proper synchronization rules:

-  Multiple readers can read **simultaneously** when no writer is active.
-  Writers have **exclusive access** (only one writer at a time).
-  No reader can read while a writer is writing.
-  No writer can write while readers are reading.
---
| Method | Behavior |
|--------|----------|
| `start_read()` | Wait while `active_writers > 0` or `waiting_writers > 0`. Then increment `active_readers`. |
| `end_read()` | Decrement `active_readers`. If zero, call `notify_all()` to wake waiting writers. |
| `start_write()` | Increment `waiting_writers`, then wait while `active_readers > 0` or `active_writers > 0`. Then decrement `waiting_writers` and set `active_writers = 1`. |
| `end_write()` | Set `active_writers = 0`. Call `notify_all()` to wake both readers and writers. |


## How to Run the Program

### Requirements
- Python 3.13.13 or higher
- No external libraries required (only standard library: `threading`, `random`, `time`)

### Execution
python readers_writers_starter.py

##Expected Output:

[Running] python -u "c:\Users\72699\Desktop\COMPX234-A2\readers_writers_starter.py"
---------------------Starting simulation(3readers 2writers)--------------
Reader 2 wants to read
Reader 2 starts reading. Active readers = 1
Reader 2 is READING
Reader 3 wants to read
Reader 3 starts reading. Active readers = 2
Reader 3 is READING
Writer 1 wants to write
Writer 1 is waiting to write.Waiting writers=1
Reader 1 wants to read
reader 1 is waiting to read
Writer 1 wants to write
Writer 1 is waiting to write.Waiting writers=2
Reader 2 stops reading.Active readers
Reader 2 finished reading
Reader 2 wants to read
reader 2 is waiting to read
Reader 3 stops reading.Active readers
No more readers - waking waiting threads
Reader 3 finished readingWriter 1 starts writing.Active writers =1
Writer 1 is WRITING

reader 2 is waiting to read
reader 1 is waiting to read
Reader 3 wants to read
reader 3 is waiting to read
Writer 1 stops writing.Active writers=0
Writer finished . Waking all waiting threads
Writer 1 finished writing
reader 3 is waiting to read
reader 1 is waiting to read
Writer 1 starts writing.Active writers =1
Writer 1 is WRITING
reader 2 is waiting to read
Writer 1 wants to write
Writer 1 is waiting to write.Waiting writers=1
Writer 1 stops writing.Active writers=0
Writer finished . Waking all waiting threads
Writer 1 starts writing.Active writers =1
Writer 1 is WRITING
reader 2 is waiting to readWriter 1 finished writing

reader 1 is waiting to read
reader 3 is waiting to read
Writer 1 wants to write
Writer 1 is waiting to write.Waiting writers=1
Writer 1 stops writing.Active writers=0
Writer finished . Waking all waiting threads
Writer 1 finished writing
reader 3 is waiting to read
Writer 1 starts writing.Active writers =1
Writer 1 is WRITINGreader 1 is waiting to read

reader 2 is waiting to read
Writer 1 stops writing.Active writers=0
Writer finished . Waking all waiting threads
Writer 1 finished writing
Reader 3 starts reading. Active readers = 1
Reader 3 is READING
Reader 1 starts reading. Active readers = 2
Reader 1 is READING
Reader 2 starts reading. Active readers = 3
Reader 2 is READING
Reader 1 stops reading.Active readers
Reader 1 finished reading
Reader 3 stops reading.Active readers
Reader 3 finished reading
Reader 2 stops reading.Active readers
No more readers - waking waiting threads
Reader 2 finished reading
Reader 3 wants to read
Reader 3 starts reading. Active readers = 1
Reader 3 is READING
Reader 1 wants to read
Reader 1 starts reading. Active readers = 2
Reader 1 is READING
Reader 2 wants to read
Reader 2 starts reading. Active readers = 3
Reader 2 is READING
Reader 3 stops reading.Active readers
Reader 3 finished reading
Reader 1 stops reading.Active readers
Reader 1 finished reading
Reader 2 stops reading.Active readers
No more readers - waking waiting threads
Reader 2 finished reading
Reader 1 wants to read
Reader 1 starts reading. Active readers = 1
Reader 1 is READING
Reader 1 stops reading.Active readers
No more readers - waking waiting threads
Reader 1 finished reading
----------------------Finish Simluiation---------------------------------

[Done] exited with code=0 in 6.232 seconds

