Qus 1.1		Write a Java program that prints all the prime numbers between 1 and 100.
Implement this using both for and while loops.

**ANS** ---> 
public class PrimeNumbers {
 public sta4c void main(String[] args) {
 System.out.println("Prime numbers between 1 and 100 using for loop:");
 printPrimesUsingForLoop();
 System.out.println("\nPrime numbers between 1 and 100 using while loop:");
 printPrimesUsingWhileLoop();
 }
 public sta4c void printPrimesUsingForLoop() {
 for (int i = 2; i <= 100; i++) {
 if (isPrime(i)) {
 System.out.print(i + " ");
 }
 }
 }
 public sta4c void printPrimesUsingWhileLoop() {
 int number = 2;
 while (number <= 100) {
 if (isPrime(number)) {
 System.out.print(number + " ");
 }
 number++;
 }
 }
 public sta4c boolean isPrime(int num) {
 if (num <= 1) {
 return false;
 }
 for (int i = 2; i <= Math.sqrt(num); i++) {
 if (num % i == 0) {
 return false;
 }
 }
 return true;
 }

Qus 1.2		Write a Java program to print Pascal's Triangle of n rows.
Use nested loops to calculate the values.

ANS --->
public class PascalTriangle {
 public sta4c void main(String[] args) {
 int numRows = 5; 
 printPascalsTriangle(numRows);
 }
 public sta4c void printPascalsTriangle(int numRows) {
 for (int i = 0; i < numRows; i++) {
 int number = 1;
 for (int j = 0; j <= i; j++) {
 System.out.print(number + " ");
 number = number * (i - j) / (j + 1);
 }
 System.out.println();
 }
 }
}

Qus 1.3		Implement the factorial calculation using recursion instead of loops.
Compare the performance and resource usage with the loop-based version.

ANS --->

import java.u4l.Scanner;
public class Factorial {
 public sta4c void main(String ar[]) {
 Scanner scanner = new Scanner(System.in);
 System.out.print("Enter a number: ");
 int n = scanner.nextInt();
 long factorial = calculate(n);
 System.out.println("Factorial of " + n + " is: " + factorial);
 scanner.close();
 }
 public sta4c long calculate(int n) {
 if (n == 0 || n == 1) {
 return 1;
 } else {
 return n * calculate(n - 1);
 }
 }
}
Qus. 1.4	Write a Java program to find and print the prime factors of a given number.

ANS --->

import java.u4l.Scanner;
public class PrimeFactors {
 public sta4c void main(String[] args) {
 Scanner scanner = new Scanner(System.in);
 System.out.print("Enter a number to find its prime factors: ");
 int number = scanner.nextInt();
 System.out.print("Prime factors of " + number + " are: ");
 findPrimeFactors(number);
 }
 public sta4c void findPrimeFactors(int number) {
 int factor = 2;
 while (number > 1) {
 if (number % factor == 0) {
 System.out.print(factor + " ");
 number /= factor;
 } else {
 factor++;
 }
 }
 }
}


Qus 2.1	Implement a command-line calculator that takes arithmetic expressions as command-line arguments and evaluates them. 
Support basic arithmetic operations like addition, subtraction, multiplication, and division. For example:	java Calculator 5 + 3

ANS --->

import java.u4l.Scanner;
public class SimpleCalculator {
 public sta4c void main(String ar[]) {
 Scanner scanner = new Scanner(System.in);
 while (true) {
 System.out.println("\nMenu:");
 System.out.println("1. Addi4on (+)");
 System.out.println("2. Subtrac4on (-)");
 System.out.println("3. Mul4plica4on (*)");
 System.out.println("4. Division (/)");
 System.out.println("5. Exit");
 System.out.print("Enter your choice: ");
 int choice = scanner.nextInt();
 if (choice == 5) {
 System.out.println("Exited...");
 break;
 }
 System.out.print("Enter 1st no.: ");
 double num1 = scanner.nextDouble();
 System.out.print("Enter 2nd no.: ");
 double num2 = scanner.nextDouble();
 double result = 0;
 switch (choice) {
 case 1:
 result = num1 + num2;
 System.out.println("Result: " + result);
 break;
 case 2:
 result = num1 - num2;
 System.out.println("Result: " + result);
 break;
 case 3:
 result = num1 * num2;
 System.out.println("Result: " + result);
 break;
 case 4:
 if (num2 != 0) {
 result = num1 / num2;
 System.out.println("Result: " + result);
 } else {
 System.out.println("Error: Division by zero.");
 }
 break;
 default:
 System.out.println("Invalid choice. Please enter a number between 1 and 5.");
 }
 }
 }
}

Qus 2.2	Implement a password generator that takes command-line arguments to specify the length of the password and which character sets to include (e.g., uppercase letters, lowercase letters, numbers, special characters).

ANS --->

import java.u4l.Random;
public class PasswordGenerator {
 public sta4c void main(String[] args) {
 if (args.length < 1) {
 System.out.println("Usage: java PasswordGenerator <length> [<includeUppercase>] 
[<includeLowercase>] [<includeNumbers>] [<includeSpecialChars>]");
 return;
 }
 int length = Integer.parseInt(args[0]);
 boolean includeUppercase = false;
 boolean includeLowercase = false;
 boolean includeNumbers = false;
 boolean includeSpecialChars = false;
 if (args.length > 1) {
 includeUppercase = Boolean.parseBoolean(args[1]);
 }
 if (args.length > 2) {
 includeLowercase = Boolean.parseBoolean(args[2]);
 }
 if (args.length > 3) {
 includeNumbers = Boolean.parseBoolean(args[3]);
 }
 if (args.length > 4) {
 includeSpecialChars = Boolean.parseBoolean(args[4]);
 }
 String password = generatePassword(length, includeUppercase, includeLowercase, 
includeNumbers, includeSpecialChars);
 System.out.println("Generated Password: " + password);
 }
 public sta4c String generatePassword(int length, boolean includeUppercase, boolean 
includeLowercase, boolean includeNumbers, boolean includeSpecialChars) {
 StringBuilder password = new StringBuilder();
 Random random = new Random();
 String uppercaseChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
 String lowercaseChars = "abcdefghijklmnopqrstuvwxyz";
 String numberChars = "0123456789";
 String specialChars = "!@#$%^&*()_-+=<>?";
 String chars = "";
 if (includeUppercase) {
 chars += uppercaseChars;
 }
 if (includeLowercase) {
 chars += lowercaseChars;
 }
 if (includeNumbers) {
 chars += numberChars;
 }
 if (includeSpecialChars) {
 chars += specialChars;
 }
 for (int i = 0; i < length; i++) {
 int randomIndex = random.nextInt(chars.length());
 password.append(chars.charAt(randomIndex));
 }
 return password.toString();
 }
}


Qus 3.1	Write a program that takes a student's score as input and prints out their corresponding grade based on the following scale:
90-100: A
80-89: B
70-79: C
60-69: D
Below 60: F 	
Implement the same with if elseif else and switch-case statements.

ANS --->

import java.u4l.Scanner;
public class Grade {
 public sta4c void main(String ar[] ) {
 Scanner sc = new Scanner(System.in);
 System.out.print("Enter student's score: ");
 int score = sc.nextInt();
 char grade;
 if (score >= 90 && score <= 100) {
 grade = 'A';
 } else if (score >= 80 && score <= 89) {
 grade = 'B';
 } else if (score >= 70 && score <= 79) {
 grade = 'C';
 } else if (score >= 60 && score <= 69) {
 grade = 'D';
 } else {
 grade = 'F';
 }
 System.out.println("Student's grade is: " + grade);
 }
}

*switch-case statements --
import java.u4l.Scanner;
public class SwitchCase {
 public sta4c void main(String ar[]) {
 Scanner sc = new Scanner(System.in);
 System.out.print("Enter student's score: ");
 int score = sc.nextInt();
 char grade;
 switch (score / 10) {
 case 10:
 case 9:
 grade = 'A';
 break;
 case 8:
 grade = 'B';
 break;
 case 7:
 grade = 'C';
 break;
 case 6:
 grade = 'D';
 break;
 default:
 grade = 'F';
 }
 System.out.println("Student's grade is: " + grade);
 }
}


Qus 3.2	Write a program that takes three integers as input representing the lengths of the sides of a triangle and determines whether the triangle is equilateral, isosceles, or scalene.

ANS --->

import java.u4l.Scanner;
public class TriangleType {
 public sta4c void main(String[] args) {
 Scanner scanner = new Scanner(System.in);
 System.out.println("Enter Value:");
 System.out.print("Side 1: ");
 int side1 = scanner.nextInt();
 System.out.print("Side 2: ");
 int side2 = scanner.nextInt();
 System.out.print("Side 3: ");
 int side3 = scanner.nextInt();
 if (side1 == side2 && side2 == side3) {
 System.out.println("The triangle is equilateral.");
 } else if (side1 == side2 || side1 == side3 || side2 == side3) {
 System.out.println("The triangle is isosceles.");
 } else {
 System.out.println("The triangle is scalene.");
 }
 scanner.close();
 }
}

Qus 3.3	Write a program that converts an amount in one currency to another based on the user's choice. The program should prompt the user to enter the amount, the source currency, and the target currency (e.g., USD to EUR). Use a switch-case statement to handle different currency conversions.

ANS --->

import java.u4l.Scanner;
public class CurrencyConverter {
 public sta4c void main(String[] args) {
 Scanner sc = new Scanner(System.in);
 System.out.print("Enter the amount: ");
 double amount = sc.nextDouble();
 System.out.print("Enter the source currency (e.g., USD, EUR, GBP): ");
 String sourceCurrency = sc.next().toUpperCase();
 System.out.print("Enter the target currency (e.g., USD, EUR, GBP): ");
 String targetCurrency = sc.next().toUpperCase();
 double convertedAmount = convertCurrency(amount, sourceCurrency, targetCurrency);
 System.out.println(amount + " " + sourceCurrency + " is equivalent to " + 
convertedAmount + " " + targetCurrency);
 }
 public sta4c double convertCurrency(double amount, String sourceCurrency, String 
targetCurrency) {
 
 double usdToEur = 0.85;
 double usdToGbp = 0.75;
 double eurToUsd = 1.18;
 double eurToGbp = 0.89;
 double gbpToUsd = 1.33;
 double gbpToEur = 1.12;
 double convertedAmount = 0;
 switch (sourceCurrency) {
 case "USD":
 switch (targetCurrency) {
 case "EUR":
 convertedAmount = amount * usdToEur;
 break;
 case "GBP":
 convertedAmount = amount * usdToGbp;
 break;
 }
 break;
 case "EUR":
 switch (targetCurrency) {
 case "USD":
 convertedAmount = amount * eurToUsd;
 break;
 case "GBP":
 convertedAmount = amount * eurToGbp;
 break;
 }
 break;
 case "GBP":
 switch (targetCurrency) {
 case "USD":
 convertedAmount = amount * gbpToUsd;
 break;
 case "EUR":
 convertedAmount = amount * gbpToEur;
 break;
 }
 break;
 }
 return convertedAmount;
 }
}

Qus 4.1	Write a program to rotate an array to the left or right by a given number of positions.

ANS --->

import java.u4l.*;
public class Array {
 public sta4c void main(String[] args) {
 int[] array = {1, 2, 3, 4, 5};
 int posi4ons = 2;
 System.out.println("Original Array: " + Arrays.toString(array));
 reverseArray(array, posi4ons);
 System.out.println("Rota4on of Array: " + Arrays.toString(array));
 }
 public sta4c void reverseArray(int[] array, int posi4ons) {
 int length = array.length;
 posi4ons %= length;
 reverseSubArray(array, 0, length - 1);
 reverseSubArray(array, 0, posi4ons - 1);
 reverseSubArray(array, posi4ons, length - 1);
 }
 public sta4c void reverseSubArray(int[] array, int start, int end) {
 while (start < end) {
 int temp = array[start];
 array[start] = array[end];
 array[end] = temp;
 start++;
 end--;
 }
 }
}


Qus 4.2	Write a program that takes an array of integers as input and removes duplicate elements, returning an array with only unique elements.

ANS --->

import java.u4l.Arrays;
import java.u4l.HashSet;
import java.u4l.Set;
public class RemoveDuplicates {
 public sta4c void main(String[] args) {
 int[] array = {1, 2, 3, 4, 2, 5, 6, 3, 7, 8, 9, 1};
 int[] uniqueArray = removeDuplicates(array);
 System.out.println("Original Array: " + Arrays.toString(array));
 System.out.println("Array with Duplicates Removed: " + Arrays.toString(uniqueArray));
 }
 public sta4c int[] removeDuplicates(int[] array) {
 Set<Integer> uniqueSet = new HashSet<>();
 for (int num : array) {
 uniqueSet.add(num);
 }
 int[] uniqueArray = new int[uniqueSet.size()];
 int index = 0;
 for (int num : uniqueSet) {
 uniqueArray[index++] = num;
 }
 return uniqueArray;
 }
}

Qus.4.3	Write a program that rotates a given N x N matrix 90 degrees clockwise.

ANS --->

import java.u4l.*;
public class MatrixRota4on {
 public sta4c void main(String[] args) {
 int[][] matrix = {
 {1, 2, 3},
 {4, 5, 6},
 {7, 8, 9}
 };
 System.out.println("Original Matrix:");
 printMatrix(matrix);
 int[][] rotatedMatrix = rotateMatrix(matrix);
 System.out.println("\nRotated Matrix:");
 printMatrix(rotatedMatrix);
 }
 public sta4c int[][] rotateMatrix(int[][] matrix) {
 int n = matrix.length;
 for (int i = 0; i < n; i++) {
 for (int j = i + 1; j < n; j++) {
 int temp = matrix[i][j];
 matrix[i][j] = matrix[j][i];
 matrix[j][i] = temp;
 }
 }
 for (int i = 0; i < n; i++) {
 int leÄ = 0, right = n - 1;
 while (leÄ < right) {
 int temp = matrix[i][leÄ];
 matrix[i][leÄ] = matrix[i][right];
 matrix[i][right] = temp;
 leÄ++;
 right--;
 }
 }
 return matrix;
 }
 public sta4c void printMatrix(int[][] matrix) {
 for (int[] row : matrix) {
 System.out.println(Arrays.toString(row));
 }
 }
}

Qus 4.4	Write a program that calculates the sum of each row and each column in a 2D matrix and displays the results.

ANS --->

import java.u4l.*;
public class MatrixSum {
 public sta4c void main(String[] args) {
 int[][] matrix = {
 {1, 2, 3},
 {4, 5, 6},
 {7, 8, 9}
 };
 System.out.println("Original Matrix:");
 printMatrix(matrix);
 int[] rowSums = calculateRowSums(matrix);
 int[] columnSums = calculateColumnSums(matrix);
 System.out.println("\nSum of Each Row:");
 System.out.println(Arrays.toString(rowSums));
 System.out.println("\nSum of Each Column:");
 System.out.println(Arrays.toString(columnSums));
 }
 public sta4c int[] calculateRowSums(int[][] matrix) {
 int numRows = matrix.length;
 int[] rowSums = new int[numRows];
 for (int i = 0; i < numRows; i++) {
 int sum = 0;
 for (int j = 0; j < matrix[i].length; j++) {
 sum += matrix[i][j];
 }
 rowSums[i] = sum;
 }
 return rowSums;
 }
 public sta4c int[] calculateColumnSums(int[][] matrix) {
 int numRows = matrix.length;
 int numCols = matrix[0].length;
 int[] columnSums = new int[numCols];
 for (int j = 0; j < numCols; j++) {
 int sum = 0;
 for (int i = 0; i < numRows; i++) {
 sum += matrix[i][j];
 }
 columnSums[j] = sum;
 }
 return columnSums;
 }
 public sta4c void printMatrix(int[][] matrix) {
 for (int[] row : matrix) {
 System.out.println(Arrays.toString(row));
 }
 }
}

Qus 4.5	Given a 2D matrix representing a map where '1's represent land and '0's represent water, write a program to count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically.

ANS --->

public class IslandCounter {
 public sta4c void main(String[] args) {
 int[][] grid = {
 {1, 1, 0, 0, 0},
 {0, 1, 0, 0, 1},
 {1, 0, 0, 1, 1},
 {0, 0, 0, 0, 0},
 {1, 0, 1, 0, 1}
 };
 System.out.println("Number of islands: " + countIslands(grid));
 }
 public sta4c int countIslands(int[][] grid) {
 if (grid == null || grid.length == 0 || grid[0].length == 0) {
 return 0;
 }
 int count = 0;
 int numRows = grid.length;
 int numCols = grid[0].length;
 for (int i = 0; i < numRows; i++) {
 for (int j = 0; j < numCols; j++) {
 if (grid[i][j] == 1) {
 count++;
 exploreIsland(grid, i, j);
 }
 }
 }
 return count;
 }
 private sta4c void exploreIsland(int[][] grid, int row, int col) {
 int numRows = grid.length;
 int numCols = grid[0].length;
 if (row < 0 || col < 0 || row >= numRows || col >= numCols || grid[row][col] == 0) {
 return;
 }
 grid[row][col] = 0;
 exploreIsland(grid, row + 1, col); // Down
 exploreIsland(grid, row - 1, col); // Up
 exploreIsland(grid, row, col + 1); // Right
 exploreIsland(grid, row, col - 1); // LeÄ
 }
}

Qus 4.6	Write a program that checks whether a given square matrix is a magic square or not. A magic square is a square matrix where the sum of each row, each column, and both diagonals is the same.

ANS --->

public class MagicSquareChecker {
 public sta4c void main(String[] args) {
 int[][] matrix = {
 {2, 7, 6},
 {9, 5, 1},
 {4, 3, 8}
 };
 System.out.println("Is the given matrix a magic square? " + isMagicSquare(matrix));
 }
 public sta4c boolean isMagicSquare(int[][] matrix) {
 int n = matrix.length;
 int sum = 0;
 for (int j = 0; j < n; j++) {
 sum += matrix[0][j];
 }
 for (int i = 1; i < n; i++) {
 int rowSum = 0;
 for (int j = 0; j < n; j++) {
 rowSum += matrix[i][j];
 }
 if (rowSum != sum) {
 return false;
 }
 }
 for (int j = 0; j < n; j++) {
 int colSum = 0;
 for (int i = 0; i < n; i++) {
 colSum += matrix[i][j];
 }
 if (colSum != sum) {
 return false;
 }
 }
 int diagonalSum1 = 0;
 for (int i = 0; i < n; i++) {
 diagonalSum1 += matrix[i][i];
 }
 if (diagonalSum1 != sum) {
 return false;
 }
 int diagonalSum2 = 0;
 for (int i = 0; i < n; i++) {
 diagonalSum2 += matrix[i][n - i - 1];
 }
 if (diagonalSum2 != sum) {
 return false;
 }
 return true;
 }
}

