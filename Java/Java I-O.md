- serialization is the process of transforming an in-memory object into a stream of bytes that can also be stored in memory or written to a file, network, database, external storage, and so on. Deserialization is the reverse process, that is, recreating the object state in memory from the given stream of bytes.
- File handler is a referance to a file that is used by the os to keep track of the file
- It is abstract representation of the file and doesn't contain any of the actual data from the file
- file resource on the other hand is the actual data from the file
- It is stored on the disk and can be accessed by os and by applications
![[Java-NIO.png]]
- NIO2 are non blocking meaning asynchronous access to resource by multiple threads
- They manage memory more efficiently by reading and writing files directly from and to memory into buffers through File Channels
-![[Comparison between Java IO and Java NIO.png]] - Java IO is stream based but Java NIO is buffer based
- A file buffer is a computer memory used to temporarily hold data while it is being read from file 
- Input stream is an abstract class representing an input stream of bytes. it represents a source of data and a common interface for reading that data
- File Reader reads directly from file which is slower
- Buffer Reader catches large block into memory called buffer and reads from it each time which makes it more performant by reducing disk I/O 
- Scanner class used for flexible input file matching using patterns
- - `Scanner` is a **text parser** — it reads raw characters from an input source (keyboard, file, string, etc.) and splits them into **tokens**.
    
- A **token** is basically a chunk of text separated by a **delimiter** (by default, any whitespace: spaces, tabs, newlines).
- ## **How `BufferedWriter` works**

When you create a `BufferedWriter`, it wraps another `Writer` (like `FileWriter` or `OutputStreamWriter`) and maintains an **internal character buffer** in memory — usually **8 KB** by default.

### Steps when writing:

1. **You call `write()`** — The text is stored in the internal buffer, **not** immediately sent to the file.
    
2. **Buffer fills up** — When the buffer reaches its capacity, `BufferedWriter` automatically **flushes** its contents to the underlying `Writer` (disk/network/etc.).
    
3. **You call `flush()`** — You can manually force writing the buffer’s current contents.
    
4. **You close the writer** — This flushes remaining data, then closes the stream.

## **How `BufferedReader` works**

When you wrap a `Reader` (like `FileReader` or `InputStreamReader`) in a `BufferedReader`, it creates an **internal character buffer** (default 8 KB).

### Steps when reading:

1. **You call `read()` or `readLine()`** — If the buffer has unread characters, it returns them **directly from memory**, without touching the disk.
    
2. **If the buffer is empty** — `BufferedReader` performs a **bulk read** from the underlying `Reader`, filling the buffer with a chunk of data (e.g., 8 KB) from disk.
    
3. **Repeat** — Reads are served from memory until the buffer is empty again.

- Buffering reduces I/O read and write by reducing system calls
- system calls are expensive
- Always read and write to files line by line to avoid Memory issues 
- Always use Buffer reader and writer than File Reader and Writer to improve performance by reducing I/O calls
- File Reader/Writer is used to write text (human readable) but Data Output/Input streams are Java I/O classes used to write values as binary data which is more efficient and light weight
- **ObjectInputStream** and **ObjectOutputStream** are Java classes used for **object serialization** — that is, converting Java objects into a stream of bytes so they can be saved to a file, sent over a network, or stored in memory — and then reconstructing those objects back from bytes.
 - In serialization transient fields are not serialized  and Serial Version Id is used to version control at serialization/deserialization process.