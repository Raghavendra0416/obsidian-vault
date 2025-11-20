- Syntax:
		File variable=new File(File Path); 
		this will create file object. folders also can be handled like files by using the folder path instead of file path.
- while entering directory path we have to use " \\(2slashs backwards)" or "/(single forward slash)". the forward and 2backward slash's works same. 
- **Absolute Path-** Full path.
- **Relative Path-** not full path, moves between directories.
- While using files it should be necessary to use exceptions. because java may throw exception while file handling.
- In Java we have to create each object for each file. 1file->1object, 2files->2objects. like this we can control the files.
- if we use "./filename" -> it will take the current path& folder & it is a relative path.
- by using file object we can also handle folders.
- Different ways reading the data from text files:
	- File Input Stream
	- Scanner
	- File Reader
	- Buffered Reader
- Files can be created, deleted in same same way for all the files but reading and writing the files will be different.
- If you want to append and overwrite the data for same file. it is best to use "try with resources" for either append or overwrite. if try with recourses are not used then the file will corrupt or will give wrong output.
##### File Input Stream:
 - **Purpose:** Reads raw bytes(int) from a file (not characters).
 - **Usage:** Good for reading binary files like images, audio, or any non-text files.
 - By typecasting we convert the byte values(or int) to characters.
 - When it reaches the end of the data in the file, it will return "-1" value.
 - It is mandatory to close the file file after reading is done (varaiableName.close();).
 - **Key Point:** It's byte-based, so not ideal for reading text files unless you process the bytes yourself.
 - Example:
	 import java.io.FileInputStream;
	 import java.io.IOException;
	 
	 public class Example {
     public static void main(String[] args) {
         try {
             FileInputStream fis = new FileInputStream("file.txt");
             int i;
             while ((i = fis.read()) != -1) {
                System.out.print((char) i); // casting bytes to characters
             }
             fis.close();
         } catch (IOException e) {
            e.printStackTrace();
         }
         }
	  }
##### Scanner:
- **Purpose:** Parses primitive types and strings using regular expressions.
- **Usage:** Often used to read input from files or the console in a human-friendly way.
- It will read the data and will return true if there is data and when it reaches the end of the data it will return false.
- It can read using sc.next() (sc- variable,next()- reads words as next token(token means word)).
- it can read using sc.nextLine() (sc- variable, nextline()- reads entire line of data).
- to check data we can use- sc.hasnext()/sc.hasnextLine().
- **Key Point:** Very convenient for reading line by line or token by token, but not the most efficient for large files.
- Example:
	 import java.io.File;
	 import java.io.FileNotFoundException;
	 import java.util.Scanner;

	 public class Example {
     public static void main(String[] args) {
        try {
            File file = new File("file.txt");
            Scanner scanner = new Scanner(file);
            while (scanner.hasNextLine()) {
                System.out.println(scanner.nextLine());
            }
            scanner.close();
         } catch (FileNotFoundException e) {
            e.printStackTrace();
         }
        }
     }
##### File Reader:
- Same as File input Stream. 
- **Purpose:** Reads characters from a file (character stream).
- When you tried to read the file it will return int but that does not mean it is int. internally it is char but at the file char cannot return anything so java will take int and will return -1 at the end of the file.
- **Usage:** Good for reading text files; unlike FileInputStream, this handles character encoding.
- **Key Point:** Character-based, but not buffered, so slower compared to BufferedReader for large files.
- Example:
	 import java.io.FileReader;
	 import java.io.IOException;

	 public class Example {
     public static void main(String[] args) {
        try {
            FileReader fr = new FileReader("file.txt");
            int i;
            while ((i = fr.read()) != -1) {
                System.out.print((char) i);
            }
            fr.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
        }
	 }
##### Buffered Reader:
- **Purpose:** Buffers input from a character stream for efficient reading.
- **Usage:** Best for reading large text files efficiently, especially line by line.
- It will read char by char and line by line.
- User convenient.
- **Key Point:** Very efficient for reading large files, especially line-by-line processing.
- Example:
	 import java.io.BufferedReader;
	 import java.io.FileReader;
	 import java.io.IOException;

	 public class Example {
     public static void main(String[] args) {
        try {
            BufferedReader br = new BufferedReader(new FileReader("file.txt"));
            String line;
            while ((line = br.readLine()) != null) {
                System.out.println(line);
            }
            br.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
        }
     }
##### Comparison:
| Class           | Reads | Type       | Best For                       |
| --------------- | ----- | ---------- | ------------------------------ |
| FileInputStream | Bytes | Binary     | Images, audio, etc.            |
| Scanner         | Text  | Token/Line | User input or simple text read |
| FileReader      | Chars | Text       | Basic reading of text files    |
| BufferedReader  | Chars | Text       | Efficient line-by-line reading |


#### Types of writing data:
- File Output Steam
- File Writer
- Buffered Writer
- Without closing or flushing the buffer, the content may never actually get written to the file because it’s still held in memory.
##### 1. FileOutputStream:
- **Purpose:** Writes **raw bytes** to a file.
- **Usage:** Ideal for writing binary data (e.g., image files, audio, etc.), but can also write text if you manually handle encoding.

```java
import java.io.FileOutputStream;
import java.io.IOException;

public class Example {
    public static void main(String[] args) {
        try {
            FileOutputStream fos = new FileOutputStream("output.txt");
            String data = "Hello, FileOutputStream!";
            fos.write(data.getBytes()); // Convert string to bytes
            fos.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

- **Key Point:** Byte-based. Not ideal for plain text unless you handle character encoding yourself.

##### 2. FileWriter:
- **Purpose:** Writes **characters** to a file.
- **Usage:** Simple and useful for writing text data.

```java
import java.io.FileWriter;
import java.io.IOException;

public class Example {
    public static void main(String[] args) {
        try {
            FileWriter fw = new FileWriter("output.txt");
            fw.write("Hello, FileWriter!");
            fw.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

- **Key Point:** Character-based. Handles basic encoding, but not the most efficient for large text.

##### 3. BufferedWriter:
- **Purpose:** Wraps around a `FileWriter` (or other `Writer`) and **buffers** the output to improve performance.
- **Usage:** Best for writing large amounts of text efficiently.

```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class Example {
    public static void main(String[] args) {
        try {
            BufferedWriter bw = new BufferedWriter(new FileWriter("output.txt"));
            bw.write("Hello, BufferedWriter!");
            bw.newLine(); // Add a new line
            bw.write("Writing efficiently.");
            bw.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

- **Key Point:** More efficient than `FileWriter` for larger files or when writing repeatedly (e.g., inside a loop).
- Imp while Using Buffer Writer:
	- It **is necessary** to use a `FileWriter` (or any other `Writer`) **with** `BufferedWriter` because:
		- **BufferedWriter doesn't write to a file on its own** — it just manages data in memory.
		- You need to tell it _where_ to eventually write that data — and that’s what `FileWriter` does: it points to the file.
		- So `BufferedWriter` **buffers** the data in memory and then **flushes it in bulk** through the `FileWriter` to the file — making it more efficient.
		- Think of `FileWriter` as a direct pipe to the file, and `BufferedWriter` as a water tank in front of the pipe. Instead of sending a drop (write) every time, the tank (buffer) stores some water (data) and sends it in bulk. More efficient!
	- **`FileWriter`** = writes characters directly to a file.
	- **`BufferedWriter`** = wraps a writer like `FileWriter` to write efficiently.
	- You pass `FileWriter` to `BufferedWriter` like this:
		BufferedWriter bw = new BufferedWriter(new FileWriter("file.txt"));
	- Can you use `BufferedWriter` alone? | ❌ No | | Can it work without `FileWriter`? | ✅ Yes, **if** you pass another valid `Writer` (e.g., to console, memory, etc.) | | Is `FileWriter` the most common? | ✅ Yes, for writing to files.


##### Comparison:

|Class|Writes|Type|Best For|
|---|---|---|---|
|FileOutputStream|Bytes|Binary|Images, files, binary content|
|FileWriter|Chars|Text|Simple text file writing|
|BufferedWriter|Chars|Text|Fast, efficient text file writing|

##### Bonus Tip

You can combine classes for better functionality. For example:

```java
BufferedWriter bw = new BufferedWriter(new FileWriter("output.txt"));
```

This gives you the **character handling of `FileWriter`** and the **speed of `BufferedWriter`**.










