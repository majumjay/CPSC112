CPSC112
=======

package edu.yale.cpsc112_assignment3;



import java.util.Random;


public class CPSC112_Assignment3 {
	
	
	 public static int exceptions = 3;
	 public static int k = 0;
	
	

  public static String mySecret = "";
  public static boolean DEBUG = true;
  public static Random r = new Random();

  public static void main(String[] args) {
    
    makeMySecret();
    
    
    isGameOver("1234");   
   isGameOver("4321");
    isGameOver("2567");
    isGameOver("1432");
   isGameOver("2346");
    isGameOver("2417");
  isGameOver("2471");
    
  
   
    
    
  }

  public static void makeMySecret() {
     // Part 1 code goes here (please leave the next few lines at the end of the makeMySecret method)
	  
	  int x;
	  int y;
	  int z;
	  int c;
	  
	  x = r.nextInt(7) +1; 
	  
	  y = r.nextInt(7) + 1; 
	  	while (y == x) 
	  		{
		    y = r.nextInt(7)+1;
	  		}
	  z = r. nextInt(7) + 1;
	  	while (z == y || z == x)
	  		{
	  		z = r.nextInt(7)+1;
	  		}
	  c = r.nextInt(7) +1; 
	  	while (c == y || c == x || c== z)
	  		{
	  		c = r.nextInt(7)+1;
	  		}
	  
	  x = x*1000;
	  y = y*100;
	  z = z*10;
	  
	  int secret = x + y + z + c;
	 

	 mySecret = ("" + secret);

	  
    if (DEBUG)
    {
       System.out.println(mySecret);
    }
    
  }
  
  
  
  public static boolean isGuessValid(String input) {
    
	  
	
	  String a = new String();
	  String b = new String();
	  String c = new String(); 
	  String d = new String();
	  
	   if (input.length() != 4) { 
		  System.out.println("Input must be a 4-digit number with digits between 1 and 7.");
		  return false;
		  
	  }
	 
	  
	  else { 
		  
	  
	  a = input.substring(0,1);
	  b = input.substring(1,2);
	  c = input.substring(2,3);
	  d = input.substring(3,4);
	  
	 try { 
	
	  int one = Integer.parseInt(a);
	  int two = Integer.parseInt(b);
	  int three = Integer.parseInt(c);
	  int four = Integer.parseInt(d);
	
	
	  if (one == two || one == three || one == four || two == three || two == four || three == four) {
		  System.out.println("Input must be a 4-digit number with digits between 1 and 7.");
		  return false;
	  }
	  
	  else if (one > 7 || two > 7 || three > 7 || four > 7) {
		  System.out.println("Input must be a 4-digit number with digits between 1 and 7.");
		  return false; 
	  }

	  else {
		  return true; 
		  
	  }
	}

	  catch (NumberFormatException e) { 
		  System.out.println("Input must be a 4-digit number with digits between 1 and 7.");
		  return false; 
	  }
}
  }
  
  
  
  public static boolean isGameOver(String input) {
    // Parts 3 and 4 code goes here
	  
	  
	  String b = new String();
	  b = input; 
	  
	  String a = new String();
	  a = mySecret; 
	  
	  int firstActual; 
	  int secondActual; 
      int thirdActual; 
	  int fourthActual;
	  
	  int firstGuess; 
	  int secondGuess; 
	  int thirdGuess; 
	  int fourthGuess;
	  
		 
	  int DigitsInCommon = 0;
	  int CorrectPosition = 0;
	  
	  int liePosition;
	  int lieInCommon = r.nextInt(5);
	  
	  				if (lieInCommon == 0) {
	  							liePosition = 0;
	  										}
	  				else if (lieInCommon == 4) {
	  					liePosition = r.nextInt(4);
	  				}
	  
	  						else {
	  							liePosition = r.nextInt(lieInCommon + 1);
	  										}
	  
	  int lie = r.nextInt(3);   
	
	  
	  if(isGuessValid(input))
	  {
		  //ACUTAL VALUES
		 firstActual =  Integer.parseInt(a.substring(0,1)); 
		 secondActual = Integer.parseInt(a.substring(1,2));
		 thirdActual = Integer.parseInt(a.substring(2,3));
		 fourthActual = Integer.parseInt(a.substring(3,4));
		  int actual = firstActual*1000 + secondActual*100 + thirdActual*10 + fourthActual;
		 
		 
		 // GUESSES
	  firstGuess = Integer.parseInt(b.substring(0,1));
		 secondGuess = Integer.parseInt(b.substring(1,2));
		 thirdGuess = Integer.parseInt(b.substring(2,3));
		 fourthGuess = Integer.parseInt(b.substring(3,4));
		 
		 int guess = firstGuess*1000 + secondGuess*100 + thirdGuess*10 + fourthGuess; 
		 
		 
		 
		 
		 	if (guess < actual) {
		exceptions = exceptions - 1; 
			if (exceptions <= 0) {
				exceptions = 0; 
			}
		System.out.println("Your guess was lower than allowed. You have " + exceptions +  " exceptions remaining.");
	}
		 
	
	
	if (exceptions == 0 && guess < actual) {
		System.out.println("Your guess was lower than allowed. You have 0 exceptions remaining.");
		return false; 
		
	}
	
	
	if (exceptions == 0 && guess > actual) {
		System.out.print("You're out of exceptions and you've guessed too high! The secret was " + mySecret +  ".");
		return true; 
	}
	
	
	
	if (actual == guess)	{ 
		System.out.println("You won!");
		firstActual = 900; 
		secondActual = 900;
		thirdActual = 900;
		fourthActual = 900;
		return true; 
	}
	
	

	
	
	
		 if (firstGuess == firstActual || firstGuess == secondActual || firstGuess == thirdActual || firstGuess == fourthActual ) {
			 DigitsInCommon = DigitsInCommon + 1; 
		 }
			  
		 
		 
		 if (firstGuess == firstActual) {
				  CorrectPosition = CorrectPosition + 1; 
			  }
		 
			  
		 if (secondGuess == firstActual || secondGuess == secondActual || secondGuess == thirdActual || secondGuess == fourthActual) {
				  DigitsInCommon = DigitsInCommon + 1;
			  }
		 
		 
		 
			  if (secondGuess == secondActual) {
				  CorrectPosition = CorrectPosition + 1; 
			  }
			  
			  
		 if (thirdGuess == firstActual || thirdGuess == secondActual || thirdGuess == thirdActual || thirdGuess == fourthActual) {
				  DigitsInCommon = DigitsInCommon + 1;
			  }
		 
			  if (thirdGuess == thirdActual) {
				  CorrectPosition = CorrectPosition + 1; 
			  }  
			  
			  

		if (fourthGuess == firstActual || fourthGuess == secondActual || fourthGuess == thirdActual || fourthGuess == fourthActual) {
				  DigitsInCommon = DigitsInCommon + 1;
			  }
		
		
		
			  if (fourthGuess == fourthActual) {
				  CorrectPosition = CorrectPosition + 1; 
			  }
			  
			  
			if (lie == 0 && k == 0) {
				System.out.print("Guess " + guess + ";");
				System.out.print(" Result: " + lieInCommon + "," + liePosition);
				System.out.println("");
				
				if (DEBUG) { 
					System.out.println("Lie");
				}
				
				k = k + 1;
				return false; 
			}
			
			
			
			if (lie == 1 || lie == 2 && k == 1) {
				k = k - 1; 
			}
			
			
			  
			  
		 
		System.out.print("Guess: " + guess + ";");
		System.out.print(" Result: " + DigitsInCommon + "," + CorrectPosition);
		System.out.println("");
		 return false; 
		 
		 
      }
	  
	  
	  
	  else 
	  {
		 return false; 
	  }
	 
	  
  }
  
  
 
  
  }
  


  

  
