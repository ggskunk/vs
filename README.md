# VanitySearch-Bitrack with FixedPaul Optimization for BTC Puzzle

# Feature

<ul>
  <li>Optimized CUDA modular math for better performance (6900 MKeys/s on 4090, 8800 MKeys/s on 5090)</li>
  <li>Less RAM usage</li>
  <li>Starting key setting function optimized with Ecc addition and batch modular inverse</li>
  <li>Easier definition of the range to scan by defining it as a power of 2</li>
  <li>Only 1 GPU allowed for better efficiency</li>
  <li>Only compressed legacy addresses</li>
</ul>

# Usage


VanitySeacrh [-v] [-gpuId] [-i inputfile] [-o outputfile] [-start HEX] [-range]

 -v: Print version
 -i inputfile: Get list of addresses to search from specified file
 -o outputfile: Output results to the specified file
 -gpuId: GPU to use, default is 0
 -start start Private Key HEX
 -range bit range dimension. start -> (start + 2^range).

```

Exemples:

./VanitySearch.exe -gpuId 0 -i input.txt -o output.txt -start 3BA89530000000000 -range 40

		[keyspace]  range=2^40
		[keyspace]  start=3BA89530000000000
		[keyspace]    end=3BA8953FFFFFFFFFF


./VanitySearch.exe -gpuId 1 -o output.txt -start 3BA89530000000000 -range 42 1MVDYgVaSN6iKKEsbzRUAYFrYJadLYZvvZ

		[keyspace]  range=2^42
		[keyspace]  start=3BA89530000000000
		[keyspace]    end=3BA8956FFFFFFFFFF


./VanitySearch.exe -gpuId 0 -start 3BA89530000000000 -range 41 1MVDYgVaSN6iKKEsbzRUAYFrYJadLYZvvZ 

		[keyspace]  range=2^41
		[keyspace]  start=3BA89530000000000
		[keyspace]    end=3BA8954FFFFFFFFFF

```
# License

VanitySearch is licensed under GPLv3.
