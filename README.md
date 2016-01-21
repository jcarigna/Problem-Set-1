# Problem-Set-1
Problem Set 1 for Data Structures



// James Carignan
// 21 Jan 2016
// Problem Set 1
// Worked with Andrew Fayed

import java.util.Arrays;
import java.util.Arrays.*;

public class Dice {

	public static void main(String[] args){
		
		boolean flag = false;
		int N = 0;
		
		//Original code from book
		
		int SIDES = 6;
		double[] dist = new double[2 * SIDES + 1];
		
		for (int i = 1; i <= SIDES; i++)
			for (int j = 1; j <= SIDES; j++)
				dist[i+j] += 1.0;
		
		for (int k = 2; k <= 2*SIDES; k++)
			dist[k] /= 36.0;
		
		//Create two new arrays to keep track of new tallies
		//and probabilities
		
		double[] numRolls = new double[2 * SIDES + 1];
		Arrays.fill(numRolls, 0.0);
		
		double[] totRolls = new double[2 * SIDES + 1];
		Arrays.fill(totRolls, 0.0);
		
		//Fills up the array with the tally of rolls
				
		while (flag != true) {
			
			int count = 0;
			
			int die1 = (int)(Math.random()*6)+1;
			int die2 = (int)(Math.random()*6)+1;

			int sum = die1 + die2;

			numRolls[sum] += 1.0;
			
		//Used to stop the loop if the prob approaches the control
		
			for (int i = 2; i < 13; i++){
			if(numRolls[i] / N >= dist[i] - .001 && numRolls[i] / N <= dist[i] + .001 && totRolls[i] == 0)
				count++;
			else
				count = 0;
			}
			
			if (count == 11)
				flag = true;
			
			N++;
			
		}
		
		int total = 0;
		for (int i = 2; i <8; i++)
			total += numRolls[i];
		
		System.out.println("Total rolls: " + total);
	
	}	
}
