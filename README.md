# BinaryListHash

A very fast hash for really big data sets

If you have millions or 10's of millions of key/value pairs then you
might need this hash tree.

**Features**

- Can use less memory than the actual total bytes of the key/value pair in some cases.
- Template driven so you can use any structure as a key.
- no costly resize operations like std::map or std::unordered_map
- maintains sort order.
- has a smaller memory foot print than std::map or std:unordered_map
- 3x faster inserts than std::map or std::unordered_map
- 5x faster reads than std::map or std::unordered_map
- 60% of memory usage of std::map or std:unordere_map (not this varies depending on the data).

**Things to Know**

- Values can only be upto 8 bytes long. This will hold a 64bit pointer, a double or a long long. If you results are larger than 8 bytes, store a pointer and perhaps use a [https://github.com/SethHamilton/HeapStack](HeapStack) to store a larger value structure,
- Inserting only acending order keys is slow. Inserting random keys performs well, inserting sequential keys performs very well.

**Perforamnce**

I'll get better performance data here soon but on my Core i7 @ 3.2Ghz I can insert 10 million 64bit keys and 64 bit values per second. I look up and retreive values at a rate of 30 million look up per second.

On large datasets generally sequential keys will result in memory consumption less than the sizeof the key + sizeof the value. On generally random keys BinaryListHash will use about 60% of the total memory that std::unordered_map will use.

**The MIT License (MIT)**

Copyright (c) 2015 Seth A. Hamilton

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
