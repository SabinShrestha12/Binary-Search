# Binary-Search
/*This is a program to search an element stored in array using binary search in which random inputs are created by program itself and searches for particular number from 10000 random inputs*/
import java.util.Random;
public class BinarySrch 
{
	public static int bnrySrch(int arr[], int x) 
    { 
        int li = 0, ri = arr.length - 1; 
        while (li <= ri) { 
            int mi = li + (ri - li) / 2; 
  
            if (arr[mi] == x) 
                return mi; 

            if (arr[mi] < x) 
                li = mi + 1; 

            else
                ri = mi - 1; 
        } 
  
        return -1; 
    } 

	public static void main(String[] args) {
		
		long start = System.currentTimeMillis();
		Random rn = new Random();
		int arr[]=new int[10000];
		int n = arr.length;
		for(int i = 0;i<10000;i++)
		{
			arr[i] = rn.nextInt(1000);
		}
		for(int i = 0; i<n-1;i++)
		{
			int minInd = i;
			for(int j = i; j<n;j++)
			{
				if(arr[j] < arr[minInd])
				{
					minInd = j;	
				}
			}
			int temp = arr[i];
			arr[i] = arr[minInd];
			arr[minInd] = temp;	
		}
		int x = 52;
		int result = bnrySrch(arr, x); 
        if (result == -1)
        {
            System.out.println("\nElement "+x+" not found");
        }
        else
        {
            System.out.println("Element "+x+" is present at "+ "index " + result);
        }
    	long end = System.currentTimeMillis();
		System.out.println("Total time taken to execute the program is : "+ (end-start)+ " ms");

	}

}


