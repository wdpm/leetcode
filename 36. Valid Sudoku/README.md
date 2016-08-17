# 36. Valid Sudoku
Determine if a Sudoku is valid, according to: Sudoku Puzzles - The Rules.

The Sudoku board could be partially filled, where empty cells are filled with the character ``'.'``.

![Sudoku.png](./images/250px-Sudoku-by-L2G-20050714.svg.png)

A partially filled sudoku which is valid.

Note:
A valid Sudoku board (partially filled) is not necessarily solvable. Only the filled cells need to be validated.
## Solution1
``` js
/**
 * @param {character[][]} board
 * @return {boolean}
 */
var isValidSudoku = function(board) {
    //Sudoku Puzzles - The Rules
    //1. Each row must have the numbers 1-9 occuring just once.
    //2. Each column must have the numbers 1-9 occuring just once.
    //3. And the numbers 1-9 must occur just once in each of the 9 sub-boxes of the grid
    //(row:) 0 1 2 3 4 5 6 7 8      
    //============================(columon:)
    //=       =        =         =0
    //=   0   =   1    =    2    =1
    //=       =        =         =2
    //============================3
    //=       =        =         =4
    //=   3   =   4    =    5    =5
    //=       =        =         =6
    //============================7
    //=       =        =         =8
    //=   6   =   7    =    8    =
    //=       =        =         =
    //============================
    
    
    
    //use two loop to traverse every cells,escape '.'
    //for every digit cell,check row,column,block constraint
    var setX=[],
        setY=[],
        setB=[];
    for(var i=0;i<9;i++){
        setX[i]=new Set();
        setY[i]=new Set();
        setB[i]=new Set();
    }
    
    for(var j=0;j<9;j++){
        for(var k=0;k<9;k++){
            if(board[j][k]==='.'){
                continue;
            }
            //row check
            if(setX[j].has(board[j][k])){
                return false;
            }else{
                setX[j].add(board[j][k]);
            }
            
            //column check
            if(setY[k].has(board[j][k])){
                return false;
            }else{
                setY[k].add(board[j][k]);
            }
            
            //sub-box check
            if(setB[parseInt(k/3)+parseInt(j/3)*3].has(board[j][k])){
                return false;
            }else{
                setB[parseInt(k/3)+parseInt(j/3)*3].add(board[j][k]);
            }
        }
    }
    
    // console.log(setX);
    // console.log(setY);
    // console.log(setB);
    return true;
};
```