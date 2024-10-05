## BINARY AND IPv4 ADDRESSES

IPv4 addresses are initially represented in binary, consisting only of 1s and 0s, making them hard for humans to manage. To simplify this, network administrators convert these binary addresses into decimal. IPv4 addresses are made up of 32 bits, divided into four 8-bit sections called octets, each separated by dots. For example, an IPv4 address like "11000000.10101000.00001010.00001010" converts to the decimal format "192.168.10.10". While binary addresses are essential for devices, humans typically use the easier-to-read dotted decimal format.

**Converting between binary and hexadecimal system**

The video explains how to convert numbers between binary and decimal systems. It starts by reviewing positional notation in the decimal system (base 10), where place values (ones, tens, hundreds, etc.) are powers of 10. For example, the number 2,168 is broken down into 2 one-thousands, 1 hundred, 6 tens, and 8 ones, adding up to 2,168.

Next, it introduces binary (base 2), where place values are powers of 2 (1, 2, 4, 8, 16, etc.), and only two characters (0 and 1) are used. The video then demonstrates how to convert decimal numbers like 168 to binary by checking which powers of 2 fit into the number and assigning a 1 or 0 accordingly.

For binary-to-decimal conversion, it explains that you sum the values of the place values where there’s a 1. For example, the binary number 011001101 converts to decimal 109.

Lastly, the video discusses converting a binary IP address (32 bits divided into 4 octets) into decimal format. Each octet is converted individually, and the final IP address example is 192.168.1.101.

A useful tool is the binary positional value table.

Is the decimal number of the octet (n) equal to or greater than the most-significant bit (128)?

If no, then enter binary 0 in the 128 positional value.
If yes, then add a binary 1 in the 128 positional value and subtract 128 from the decimal number. And so on for each position.

**Hexadecimal and IPv6 Addresses**

To work with IPv6 addresses, you need to understand how hexadecimal (base 16) works in relation to binary and decimal. Hexadecimal uses the digits 0-9 and the letters A-F to represent values, making it more compact than binary. For instance:

Binary: 0000 to 1111 (4 bits)
Hexadecimal: 0 to F (single digit)
Since each hexadecimal digit corresponds to 4 binary bits, IPv6 addresses, which are 128 bits long, are represented using 32 hexadecimal characters. IPv6 addresses are written in the format x:x:x:x:x:x:x
, where each "x" represents a 16-bit segment (hextet), corresponding to four hexadecimal digits.

Example Conversion:
To convert a binary value to hexadecimal, group the binary digits into 4-bit chunks:

Binary: 1010 1100 becomes Hexadecimal: AC
IPv6 addresses are often used in networking, and the compact hexadecimal format makes reading and writing them easier. IPv6 addresses can be written in either lowercase or uppercase, and a single hextet (group of 4 hexadecimal digits) represents 16 bits of the address.

This knowledge is essential for understanding both IPv6 addressing and Ethernet MAC addresses.

Hexadecimal (hex) is a base 16 number system, using digits 0-9 and letters A-F. To convert between hex and decimal, we use positional notation, where each position is a power of 16. The first four place values are:

16^0 =1
16^1=16
16^2= 256
16^3 = 4096

Each hex digit represents 4 binary bits, making it easier to convert between hex and binary. An 8-bit binary number can be represented by two hex digits.

