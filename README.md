## IP Address Library:

This is the work I did when working on TCP/IP assignments. Particularly the ones dealing with IP addresses and subnets.
This library contains an easy and convenient, albeit not the most efficient, implementation of IP address operations.

### Note :

I made the library more for educational and academic reasons than for any actual use. And as such, I'm open sourcing it with the intention that someone else may find it useful while learning IP addresses.

### Dependencies :

1. Python 3 runtime environment.

### Usage :

There are two main classes that can be used to compute IP address operations. 
1. IPConv
2. Subnet

#### IPConv:

This class is used for all operations related to IP addresses.

* An object can be instantiated by passing the IP address in one of these forms- 
```dotted-decimal, binary, hexadecimal or CIDR notation```

```ip = IPConv('127.0.0.1/8')``` 

* Once the object has been created, you can convert this into any alternate notation by-
```
ip.hexadecimal() # 7F:00:00:01
ip.dotted_decimal() # 127.0.0.1
ip.binary() # 01111111000000000000000000000001
```

* You can print all relevant info regarding the IP address by doing-
```
ip.desc()

Dotted-Decimal      : 127.0.0.1
Binary              : 01111111000000000000000000000001
Hexadecimal         : 7F:00:00:01

Classful Addressing Scheme:
Class               : A
Network mask        : 8
Range               : 16777216
Network address     : 127.0.0.0
Broadcast address   : 127.255.255.255

Classless Addressing Scheme:
Network mask        : 8
Range               : 16777216
Network address     : 127.0.0.0
Broadcast address   : 127.255.255.255
```

* You can also get the next or prev IP address from the original address as follows-
```
for i in ip.next(5):
	print(i)

for i in ip.prev(5):
	print(i)
```

#### Subnet:

This class is used for working with subnets. Note that this implementation is for classless IP addressing. But since classful IP addressing can be considered as a special case of classless, it is compatible with both of them. You just need to give correct mask.

* Initalizing a Subnet object requires two things- IP address in CIDR notation and number of subnets you want.
```
snet = Subnet('127.0.0.1/8', 8)
```

* You can get a table of all the IP ranges by doing-
```
snet.desc()

+===================================================================+
|Index  |First Address      |Last Address       |Range              |
+===================================================================+
|1      |127.0.0.0          |127.31.255.255     |2097152            |
---------------------------------------------------------------------
|2      |127.32.0.0         |127.63.255.255     |2097152            |
---------------------------------------------------------------------
|3      |127.64.0.0         |127.95.255.255     |2097152            |
---------------------------------------------------------------------
|4      |127.96.0.0         |127.127.255.255    |2097152            |
---------------------------------------------------------------------
|5      |127.128.0.0        |127.159.255.255    |2097152            |
---------------------------------------------------------------------
|6      |127.160.0.0        |127.191.255.255    |2097152            |
---------------------------------------------------------------------
|7      |127.192.0.0        |127.223.255.255    |2097152            |
---------------------------------------------------------------------
|8      |127.224.0.0        |127.255.255.255    |2097152            |
---------------------------------------------------------------------
```

* You can get the first or last subnets by-
```
for i in snet.first(5):
    print(i)

for i in snet.last(5):
	print(i)
```

### License :

This project is licensed under the terms of the MIT license.

