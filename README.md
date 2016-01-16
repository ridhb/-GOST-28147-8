# -GOST-28147-8
The GOST block cipher, defined in the standard GOST 28147-89, is a Soviet and Russian government standard symmetric key block cipher. GOST has a 64-bit block size and a key length of 256 bits. Its S-boxes can be secret, and they contain about 354 (log2(16!8)) bits of secret information, so the effective key size can be increased to 610 bits; however, a chosen-key attack can recover the contents of the S-Boxes in approximately 232 encryptions.[2]

GOST is a Feistel network of 32 rounds. Its round function is very simple: add a 32-bit subkey modulo 232, put the result through a layer of S-boxes, and rotate that result left by 11 bits. The result of that is the output of the round function. In the diagram to the right, one line represents 32 bits.

The subkeys are chosen in a pre-specified order. The key schedule is very simple: break the 256-bit key into eight 32-bit subkeys, and each subkey is used four times in the algorithm; the first 24 rounds use the key words in order, the last 8 rounds use them in reverse order.

The S-boxes accept a four-bit input and produce a four-bit output. The S-box substitution in the round function consists of eight 4 × 4 S-boxes. The S-boxes are implementation-dependent – parties that want to secure their communications using GOST must be using the same S-boxes. For extra security, the S-boxes can be kept secret. In the original standard where GOST was specified, no S-boxes were given, but they were to be supplied somehow. This led to speculation that organizations the government wished to spy on were given weak S-boxes
https://en.wikipedia.org/wiki/GOST_(block_cipher)

java : GOST-28147-8/gost.java

