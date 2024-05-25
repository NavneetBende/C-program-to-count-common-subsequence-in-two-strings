Counting Common Subsequence in two String.
In this article we will learn how to write a C program to Count Common Subsequence In Two Strings. Subsequence are the part of sequence (‘a’, ‘b’, ‘ab’ are the subsequence of ‘ab’). So we will be taking two string as an input here and then we will find out the subsequence of each string and then we will count the common subsequence and will print this count as an output.

C programming code to count common subsequence in two strings 
Algorithm:
Initialize the variables.
Accept the inputs.
Create a function to check common subsequence
Take each character from  the first string and match it with the second string.
If they matches store the count.
Print count.
C programming code to count common subsequence in two strings 
C programming code to count common subsequence in two strings 
Run
//Count Common Subsequence In Two Strings
#include <stdio.h>
#include <string.h>

//Function to count the number of subsequences in the string.
int countsequences(char str[], char str2[])
{
  int n1 = strlen(str);
  int n2 = strlen(str2);
  int cnt[n1+1][n2+1];
  for (int i = 0; i <= n1; i++)  
  { 
    for (int j = 0; j <= n2; j++)
    {
      cnt[i][j] = 0;
    }
  }
  //Taking each character from first string.
  for (int i = 1; i <= n1; i++)
  {
  //Taking each character from second string.
  for (int j = 1; j <= n2; j++)
  {
  //If characters are same in both the string.

  if(str[i-1] == str2[j-1])
  {
    cnt[i][j] = 1 + cnt[i][j-1] + cnt[i-1][j];
  }
  else
  {
    cnt[i][j] = cnt[i][j-1] + cnt[i-1][j] - cnt[i-1][j-1];
    }
  }
}
 return cnt[n1][n2];
}
//Main function for printing the result.
int main()
{
  char str[100]="Prepinsta" ,str2[100]="Prep";

  printf("Number of common subsequence is: %d ",countsequences(str, str2));
  return 0;
}
