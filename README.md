# Hash Tables

Ex. (17) - <strong>Hash table</strong> membership test structure appears here in Python. Though the syntax is Python-specific, the core idea stays identical. This snippet belongs to the set of 127 algorithms in <i><a href="https://github.com/Gagniuc/Antivirus-Engines">Antivirus Engines: From Methods to Innovations, Design, and Applications</a></i> (Elsevier Syngress, 2024).

***

This repository contains a minimal implementation of a <i><a href="https://www.mdpi.com/1999-4893/18/12/804">Hash Table</a></i> in Python using <i>separate chaining</i> to handle collisions. The class <i>H</i> is initialized with a fixed table size and internally stores data in a list of lists. The method <i>_h</i> represents the hash function, which computes the index of a given key by applying the Python built-in <i>hash()</i> function followed by the modulo operator to ensure the index falls within the table size. The method <i>i</i> is responsible for inserting key-value pairs into the table by appending them to the appropriate list at the computed index. The method <i>f</i> allows searching for a value by its key by first locating the index using the same hash function and then iterating through the stored pairs to find a match. If the key exists, the corresponding value is returned, otherwise <i>None</i> is returned. The repository also contains an example where the hash table is created with a size of 10, and three key-value pairs are inserted, mapping string keys to malware categories such as <i>Trojan</i>, <i>Rootkit</i>, and <i>Bootkit</i>. Subsequent searches demonstrate the functionality, showing successful retrieval of existing values and a <i>None</i> result when searching for a missing key. Thus, this project highlights the core principles of hash tables, including hashing, collision handling, insertion, and lookup.

## Native implementation in Python

```python
class H:
    def __init__(s, n):
        s.n = n
        s.t = [[] for _ in range(n)]

    def _h(s, k):
        return hash(k) % s.n

    def i(s, k, v):
        idx = s._h(k)
        s.t[idx].append((k, v))

    def f(s, k):
        idx = s._h(k)
        for x, y in s.t[idx]:
            if x == k:
                return y
        return None


# create a hash table and insert
# some key-value pairs:

h = H(n=10)
h.i("d41d8cd98f00b204e9800998ecf8427e", "Trojan")
h.i("098f6bcd4621d373cade4e832627b4f6", "Rootkit")
h.i("1f0e3dad99908345f7439f8ffabdffc4", "Bootkit")

# search for values using keys:
print(h.f("d41d8cd98f00b204e9800998ecf8427e"))
print(h.f("098f6bcd4621d373cade4e832627b4f6"))
print(h.f("1f0e3dad99908345f7439f8ffabdffc4"))
print(h.f("c4ca4238a0b923820dcc509a6f75849b"))
``` 

```text
Output:
Trojan
Rootkit
Bootkit
None
```

## References

- <i>Paul A. Gagniuc. Antivirus Engines: From Methods to Innovations, Design, and Applications. Cambridge, MA: Elsevier Syngress, 2024. pp. 1-656.</i>
- <i>Gagniuc, P. A., & Togan, M. (2025). Hash Tables as Engines of Randomness at the Limits of Computation: A Unified Review of Algorithms. Algorithms, 18(12), 804.</i>

***

<a href="https://www.mdpi.com/1999-4893/18/12/804">
  <kbd>
    <img src="https://github.com/Gagniuc/Hash-table/blob/main/src/abstract.png" alt="Hash Tables as Engines of Randomness at the Limits of Computation: A Unified Review of Algorithms">
  </kbd>
</a>
