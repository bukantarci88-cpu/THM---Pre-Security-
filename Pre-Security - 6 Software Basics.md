# Pre-Security - 6. Software Basics

### **1. Data Representation**

- **Decimal (Base-10) system**: This is the system we use in our everyday life.
- **Binary (Base-2) system**: Computers understand two states, which are encoded as `0` and `1`.
- **Hexadecimal (Base-16) system**: Every 4 binary digits (bits) can be grouped as one hexadecimal digit. A hexadecimal digit ranges between `0` and `F`.
- **Octal (Base-8) system**: Every 3 binary digits (bits) can be grouped as one octal digit. An octal digit ranges between `0` and `7`. This one is less commonly encountered on computer systems.

Moreover, how a color can be represented.

- **Bit**: It is short for binary digit, and it can be either `0` or `1`.
- **Byte**: On modern systems, a byte is 8 bits. It is also referred to as an **octet**.
- **Hex color**: A color is represented as a combination of red, green, and blue on computer systems. If one byte is assigned for each of the primary colors (red, green, and blue), we can get more than 16 million color combinations.

### 2. Data Encoding

ASCII (**American Standard Code for Information Interchange**) is a 7-bit character encoding standard that represents **128 unique characters** (0–127), including English letters, digits, punctuation, and control codes. 

**1. Limited Character Set** The most critical drawback is its inability to represent characters outside the basic English alphabet. ASCII cannot encode **accented letters**, **non-Latin scripts** (e.g., Chinese, Arabic), or many **special symbols**. This makes it unsuitable for multilingual applications and globalized systems.

**2. Fixed Size Restriction** Standard ASCII uses **7 bits**, allowing only 128 characters. Even **Extended ASCII** (8 bits) supports only 256 characters, which is still far from covering the **149,000+ characters** in Unicode. This limitation forces developers to rely on alternative encodings for broader language support.

**3. Lack of Standardization in Extended ASCII** Extended ASCII varies between platforms (e.g., Windows-1252 vs. ISO-8859-1), leading to **compatibility issues** when exchanging data between systems. A character in one extended set may map to a different symbol in another.

**4. No Support for Complex Scripts** ASCII cannot handle **right-to-left languages**, **combining characters**, or **emoji**. Modern applications require encodings like **UTF-8** to represent such characters reliably.

**5. Legacy System Constraints** While ASCII is still used in **protocols, file formats, and command-line interfaces**, its limitations mean it often serves only as a **fallback** when Unicode or other encodings fail.

Three encoding standards: UTF-8, UTF-16, and UTF-32.

- **UTF-8** uses 1–4 bytes per character and is dominant on the web.
- **UTF-16** uses 2 or 4 bytes per character and is common in **Windows**, **Java**, **.NET**, and **JavaScript** string storage.
- UTF-16 can be more memory-efficient for text with many non-Latin characters but less so for ASCII-heavy text.