//zohopuzzlebasedprogram






 public class Solution { 
     public int CalculateMinimumHP(int[][] dungeon)
    {
        if(dungeon == null || dungeon.Length == 0) return 0;
        int row = dungeon.Length; int col = dungeon[0].Length; int[,] dp = new int[row,col];
        if(dungeon[row-1][col-1] >= 1)
        { 
            dp[row-1,col-1] = 1;
        } 
        else { dp[row-1,col-1] = 1 - dungeon[row-1][col-1]; 
            
        } // for last column
        for(int i = row-2 ; i >=0 ; i--)
        { 
            if(dungeon[i][col-1] >= dp[i+1,col-1])
            { 
                dp[i,col-1] = 1;
                } 
                else 
                { 
                    dp[i,col-1] = dp[i+1,col-1] - dungeon[i][col-1];
                    } } // for last row
                    for(int j = col-2 ;j >= 0 ; j--)
                    { 
                        if(dungeon[row-1][j] >= dp[row-1,j+1]) 
                        {
                            dp[row-1,j] = 1; 
                            
                        } 
                        else 
                        { 
                            dp[row-1,j] = dp[row-1,j+1] - dungeon[row-1][j];
                            } 
                        
                    } 
                    for(int i = row-2 ; i >= 0 ; i--) 
                    { 
                        for(int j = col-2 ; j >= 0 ; j--)
                        { 
                    int valueToMoveRight = 0;
                    int valueToMoveDown = 0; // For move to right 
                    if(dungeon[i][j] > dp[i,j+1]) 
                    { 
                        valueToMoveRight = 1; 
                        
                    } 
                    else 
                    {
                        valueToMoveRight = dp[i,j+1] - dungeon[i][j]; 
                        
                    } // For move to down 
                    if(dungeon[i][j] > dp[i+1,j]) 
                    { 
                        valueToMoveDown = 1; 
                        
                    } 
                    else 
                    { 
                        valueToMoveDown = dp[i+1,j] - dungeon[i][j];
                        } 
                        dp[i,j] = Math.Min(valueToMoveRight,valueToMoveDown);
                        } 
                        
                    } 
                    return dp[0,0]; 
        
    } 
    
}
