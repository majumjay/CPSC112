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
  

  
