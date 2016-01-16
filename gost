package GOST;
//2016
//Ridho Bustami
//Adapted from C++ by Colin Plumb, 
//The Soviet GOST algorithm (without the correct S-boxes). https://www.schneier.com/sccd/GOST-PLU.ZIP

public class gost {
	 
	private static int k8 [] ={
		14,  4, 13,  1,  2, 15, 11,  8,  3, 10,  6, 12,  5,  9,  0,  7 };
	private static int k7 [] = {
		15,  1,  8, 14,  6, 11,  3,  4,  9,  7,  2, 13, 12,  0,  5, 10 };
	private static int  k6 [] = {
		10,  0,  9, 14,  6,  3, 15,  5,  1, 13, 12,  7, 11,  4,  2,  8 };
	private static int  k5[] = {
		 7, 13, 14,  3,  0,  6,  9, 10,  1,  2,  8,  5, 11, 12,  4, 15 };
	private static int  k4[] = {
		 2, 12,  4,  1,  7, 10, 11,  6,  8,  5,  3, 15, 13,  0, 14,  9 };
	private static int k3[] = {
		12,  1, 10, 15,  9,  2,  6,  8,  0, 13,  3,  4, 14,  7,  5, 11 };
	private static int  k2[] = {
		 4, 11,  2, 14, 15,  0,  8, 13,  3, 12,  9,  7,  5, 10,  6,  1 };
	private static int  k1[] = {
		13,  2,  8,  4,  6, 15, 11,  1, 10,  9,  3, 14,  5,  0, 12,  7 };
	
	static int[] k87 = new int  [256];
	static int[] k65 = new int  [256];
	static int[] k43 = new int  [256];
	static int[] k21 = new int  [256];

	public static void kboxinit() {
		 for (int i = 0; i < 256; i++) {
				k87[i] = (int) (k8[i >> 4] << 4 | k7[i & 15]);
				k65[i] = (int) (k6[i >> 4] << 4 | k5[i & 15]);
				k43[i] = (int) (k4[i >> 4] << 4 | k3[i & 15]);
				k21[i] = (int) (k2[i >> 4] << 4 | k1[i & 15]);
			}	 
	 }
	 
	 private static int f(int x){
		 x = (int) (k87[(int) (x>>24 & 255)] << 24 | k65[(int) (x>>16 & 255)] << 16 |
				    k43[(int) (x>> 8 & 255)] <<  8 | k21[(int) (x & 255)]);
		 return (int) (x<<11 | x>>(32-11));
	 }
	 
	 public static void encrypt(int[] in, int[] out, int[] key) {
		 	int n1 = in[0];
		 	int n2 = in[1];
			n2 ^= f((int) (n1+key[0]));
			n1 ^= f((int) (n2+key[1]));
			n2 ^= f((int) (n1+key[2]));
			n1 ^= f((int) (n2+key[3]));
			n2 ^= f((int) (n1+key[4]));
			n1 ^= f((int) (n2+key[5]));
			n2 ^= f((int) (n1+key[6]));
			n1 ^= f((int) (n2+key[7]));

			n2 ^= f((int) (n1+key[0]));
			n1 ^= f((int) (n2+key[1]));
			n2 ^= f((int) (n1+key[2]));
			n1 ^= f((int) (n2+key[3]));
			n2 ^= f((int) (n1+key[4]));
			n1 ^= f((int) (n2+key[5]));
			n2 ^= f((int) (n1+key[6]));
			n1 ^= f((int) (n2+key[7]));

			n2 ^= f((int) (n1+key[0]));
			n1 ^= f((int) (n2+key[1]));
			n2 ^= f((int) (n1+key[2]));
			n1 ^= f((int) (n2+key[3]));
			n2 ^= f((int) (n1+key[4]));
			n1 ^= f((int) (n2+key[5]));
			n2 ^= f((int) (n1+key[6]));
			n1 ^= f((int) (n2+key[7]));

			n2 ^= f((int) (n1+key[7]));
			n1 ^= f((int) (n2+key[6]));
			n2 ^= f((int) (n1+key[5]));
			n1 ^= f((int) (n2+key[4]));
			n2 ^= f((int) (n1+key[3]));
			n1 ^= f((int) (n2+key[2]));
			n2 ^= f((int) (n1+key[1]));
			n1 ^= f((int) (n2+key[0]));
		
			/* There is no swap after the last round */
			out[0] = n2;
			out[1] = n1;
			
	 }
	
	 public static void decrypt(int[] in, int[] out, int[] key) {
			int n1 = in[0];
			int n2 = in[1];

			n2 ^= f((int) (n1+key[0]));
			n1 ^= f((int) (n2+key[1]));
			n2 ^= f((int) (n1+key[2]));
			n1 ^= f((int) (n2+key[3]));
			n2 ^= f((int) (n1+key[4]));
			n1 ^= f((int) (n2+key[5]));
			n2 ^= f((int) (n1+key[6]));
			n1 ^= f((int) (n2+key[7]));

			n2 ^= f((int) (n1+key[7]));
			n1 ^= f((int) (n2+key[6]));
			n2 ^= f((int) (n1+key[5]));
			n1 ^= f((int) (n2+key[4]));
			n2 ^= f((int) (n1+key[3]));
			n1 ^= f((int) (n2+key[2]));
			n2 ^= f((int) (n1+key[1]));
			n1 ^= f((int) (n2+key[0]));

			n2 ^= f((int) (n1+key[7]));
			n1 ^= f((int) (n2+key[6]));
			n2 ^= f((int) (n1+key[5]));
			n1 ^= f((int) (n2+key[4]));
			n2 ^= f((int) (n1+key[3]));
			n1 ^= f((int) (n2+key[2]));
			n2 ^= f((int) (n1+key[1]));
			n1 ^= f((int) (n2+key[0]));

			n2 ^= f((int) (n1+key[7]));
			n1 ^= f((int) (n2+key[6]));
			n2 ^= f((int) (n1+key[5]));
			n1 ^= f((int) (n2+key[4]));
			n2 ^= f((int) (n1+key[3]));
			n1 ^= f((int) (n2+key[2]));
			n2 ^= f((int) (n1+key[1]));
			n1 ^= f((int) (n2+key[0]));

			out[0] = n2;
			out[1] = n1;
			
	 }
	 
	   public static void main (String[] args) {
		 //test 
		 int [] key = {1,2, 3, 7, 5, 200, 7, 8};
		 int[] plain = {-200,89};
		 int[] cipher= {0,0};
		 int[] plain2 = {0,0};

		 kboxinit();
		 encrypt(plain, cipher, key);
		 decrypt(cipher, plain2, key);
		 
		 System.out.print(plain[0]);
		 System.out.print(",");
		 System.out.print(plain[1]);
		 System.out.println();
		 System.out.print(plain2[0]);
		 System.out.print(",");
		 System.out.print(plain2[1]);
		 
	 }
	

}
