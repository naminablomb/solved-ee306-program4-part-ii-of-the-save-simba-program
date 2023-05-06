Download Link: https://assignmentchef.com/product/solved-ee306-program4-part-ii-of-the-save-simba-program
<br>
This is Part II of the​<em> Save Simba</em>​ program you worked on in Program 3.  In this part, you will make your program interactive. The player guides Simba home by avoiding Hyenas and preventing him from falling off the Jungle Grid. The movement is taken as an input and the Jungle Grid is appropriately updated.

Details

We pick up where Part I left off. We now have a jungle that is loaded from a linked list giving us the coordinates of where Simba is and the destination (Home) he needs to reach. You will take input from

the user, which is a keystroke (i,j,k or l) which conveys the intended direction to move Simba. You will verify if the user entered a valid keystroke, check if the move is a safe one, apply it or report otherwise. The process is repeated with each move, causing Simba’s position being updated in the Jungle Grid and displayed on the console. The program ends when Simba reaches Home – which is a check you are asked to perform.




The main program that is the engine of your game is provided to you along with the declaration of the GRID​ and several variables. You will need the subroutines you wrote for Program 3 and complete four new subroutines.




<h1>Your Task / Subroutines</h1>

Implement the following ​<strong>four </strong>​subroutines. Three of these subroutines are called by my code, the other (​SAFE_MOVE​) is a routine that is called from one of your subroutines. This routine will be independently tested  just like ​GRID_ADDRESS​ from the Part I.

<ul>

 <li>IS_INPUT_VALID​: This subroutine validates the player move to make sure it is one of the movement characters. All it does is check if a valid character is entered.

  <ul>

   <li>Inputs: ​R0​ – a move represented by ‘i’, ‘j’, ‘k’, or ‘l’</li>

  </ul></li>

</ul>

○ Outputs: ​R2​ – 0 = valid; -1 = invalid

<ul>

 <li>SAFE_MOVE​: This subroutine checks if a move is safe and returns the new position where Simba would go to if the move is safe. An unsafe move is one of the following cases:

  <ul>

   <li>movement to a location where there is a hyena</li>

  </ul></li>

</ul>

○ movement off the grid; this can happen in any direction.

In coding this routine you will need to translate a move to coordinates using ​GRID_ADDRESS​. Your ​APPLY_MOVE ​subroutine calls this subroutine to check whether a move is safe before applying it to the ​GRID​.

○ Inputs: ​R0​ – a move represented by ‘i’, ‘j’, ‘k’, or ‘l’

○ Outputs: ​R1​, ​R2​ – the new row and new col, respectively; if the move is to an unsafe (hyena or outside the ​GRID​), ​R1​ = -1

Note: This subroutine does not check if the input (R0​​      ) is valid. You have to implement this functionality elsewhere. Also, this routine does not make any updates to the GRID or Simba’s position. These are the job of the APPLY_MOVE ​​        function.

<ul>

 <li>APPLY_MOVE​: This subroutine makes the move if it can be completed. It checks to see if the movement is safe by calling SAFE_MOVE ​​ which returns the coordinates of where the move goes (or -1 if movement is unsafe as detailed below). If the move is Safe then this routine moves the player symbol to the new coordinates and clears any walls (|’s and -’s) as necessary for the movement to take place. If the movement is unsafe, output a console message of your choice and return.

  <ul>

   <li>Input: R0 has move (i or j or k or l)</li>

  </ul></li>

</ul>

○ Output: None; However, must update the GRID ​​ and change CURRENT_ROW ​​     and CURRENT_COL ​if move is successfully applied.

Notes:  Calls SAFE_MOVE ​​ and GRID_ADDRESS​




<ul>

 <li>IS_SIMBA_HOME​: Checks to see if the Simba has reached Home. ○ Inputs: <em>none</em>​

  <ul>

   <li>Outputs: R2​​ is zero if Simba is Home; -1 otherwise</li>

  </ul></li>

</ul>

<h1>Testrun</h1>

Here is the console output for a sample run where the Jungle loaded was the same as shown in Program3. Only the first four and the last three Grid views are shown below. The complete sample run is given in this file: <a href="https://drive.google.com/open?id=17JkgGRYQn1zIza-N5ek9d5n-1HpslGEJ">SampleRunConsole.tx</a><u>​   </u><a href="https://drive.google.com/open?id=17JkgGRYQn1zIza-N5ek9d5n-1HpslGEJ">t</a>







0 1 2 3 4 5 6 7

+-+-+-+-+-+-+-+-


<ul>

 <li>| | | | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| | | | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| | | | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| | | | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| | | | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| | | | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| | | | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| | | | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-





Jungle Initial




0 1 2 3 4 5 6 7

+-+-+-+-+-+-+-+-


<ul>

 <li>| |#| | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| |#| | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| |*| | | | | | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| | | | | |#| | |</li>

</ul>

+-+-+-+-+-+-+-+-


<ul>

 <li>| | | | |#| | |H|</li>

</ul>




<table width="624">

 <tbody>

  <tr>

   <td width="624">  +-+-+-+-+-+-+-+-+5         | | | | | | |#| |+-+-+-+-+-+-+-+-+6         | | | |#| | | | |+-+-+-+-+-+-+-+-+7         | | | | | | | | |   +-+-+-+-+-+-+-+-+ Jungle Loaded Enter Move(up(i) left(j),down(k),right(l)): iUnSafe Move 0 1 2 3 4 5 6 7+-+-+-+-+-+-+-+-+0         | |#| | | | | | |+-+-+-+-+-+-+-+-+1         | |#| | | | | | |+-+-+-+-+-+-+-+-+2         | |*| | | | | | |+-+-+-+-+-+-+-+-+3         | | | | | |#| | |+-+-+-+-+-+-+-+-+4         | | | | |#| | |H|+-+-+-+-+-+-+-+-+5         | | | | | | |#| |+-+-+-+-+-+-+-+-+6         | | | |#| | | | |+-+-+-+-+-+-+-+-+7         | | | | | | | | |   +-+-+-+-+-+-+-+-+ Enter Move(up(i) left(j),down(k),right(l)): j0 1 2 3 4 5 6 7+-+-+-+-+-+-+-+-+0         | |#| | | | | | |+-+-+-+-+-+-+-+-+1         | |#| | | | | | |+-+-+-+-+-+-+-+-+2         |*  | | | | | | |+-+-+-+-+-+-+-+-+3         | | | | | |#| | |+-+-+-+-+-+-+-+-+4         | | | | |#| | |H|+-+-+-+-+-+-+-+-+5         | | | | | | |#| |+-+-+-+-+-+-+-+-+6         | | | |#| | | | |+-+-+-+-+-+-+-+-+7         | | | | | | | | |   +-+-+-+-+-+-+-+-+ .. (skipped) . Enter Move(up(i) left(j),down(k),right(l)): l0 1 2 3 4 5 6 7+-+-+-+-+-+-+-+-+0 | |#| | | | | | |+-+-+-+-+-+-+-+-+</td>

  </tr>

  <tr>

   <td width="624">1         | |#| | | | | | |+-+-+-+-+-+-+-+-+2         |   | | |      *|+ +-+-+-+ +-+-+-+3         | | |     |#| | |+ +-+ +-+-+-+-+-+4         |     | |#| | |H|+-+-+-+-+-+-+-+-+5         | | | | | | |#| |+-+-+-+-+-+-+-+-+6         | | | |#| | | | |+-+-+-+-+-+-+-+-+7         | | | | | | | | |   +-+-+-+-+-+-+-+-+ Enter Move(up(i) left(j),down(k),right(l)): k0 1 2 3 4 5 6 7+-+-+-+-+-+-+-+-+0         | |#| | | | | | |+-+-+-+-+-+-+-+-+1         | |#| | | | | | |+-+-+-+-+-+-+-+-+2         |   | | |       |+ +-+-+-+ +-+-+ +3         | | |     |#| |*|+ +-+ +-+-+-+-+-+4         |     | |#| | |H|+-+-+-+-+-+-+-+-+5         | | | | | | |#| |+-+-+-+-+-+-+-+-+6         | | | |#| | | | |+-+-+-+-+-+-+-+-+7         | | | | | | | | |   +-+-+-+-+-+-+-+-+ Enter Move(up(i) left(j),down(k),right(l)): k0 1 2 3 4 5 6 7+-+-+-+-+-+-+-+-+0         | |#| | | | | | |+-+-+-+-+-+-+-+-+1         | |#| | | | | | |+-+-+-+-+-+-+-+-+2         |   | | |       |+ +-+-+-+ +-+-+ +3         | | |     |#| | |+ +-+ +-+-+-+-+ +4         |     | |#| | |*|+-+-+-+-+-+-+-+-+5         | | | | | | |#| |+-+-+-+-+-+-+-+-+6         | | | |#| | | | |+-+-+-+-+-+-+-+-+7         | | | | | | | | |   +-+-+-+-+-+-+-+-+ You Saved Simba !Goodbye! —– Halting the processor —– </td>

  </tr>

 </tbody>

</table>


