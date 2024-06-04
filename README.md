# codeAlpha_task1
#include <iostream>
// N is the size of the 2D matrix N*N
#define H 9
using namespace std;
/* A utility function to print grid */
void print(int arr[H][H])
{
	for (int i = 0; i < H; i++) 
	{
		for (int j = 0; j < H; j++)
			cout << arr[i][j] << " ";
		cout << endl;
	}
}
bool isSafe(int grid[H][H], int row, 
					int col, int num)
{
	
	for (int x = 0; x <= 8; x++)
		if (grid[row][x] == num)
			return false;
	for (int x = 0; x <= 8; x++)
		if (grid[x][col] == num)
			return false;
	int startRow = row - row % 3, 
			startCol = col - col % 3;

	for (int i = 0; i < 3; i++)
		for (int j = 0; j < 3; j++)
			if (grid[i + startRow][j + 
							startCol] == num)
				return false;

	return true;
}

bool solvingSudoku(int grid[H][H], int row, int col)
{
	
	if (row == H - 1 && col == H)
		return true;

	if (col == H) {
		row++;
		col = 0;
	}

	if (grid[row][col] > 0)
		return solvingSudoku(grid, row, col + 1);

	for (int num = 1; num <= H; num++) 
	{

		if (isSafe(grid, row, col, num)) 
		{
			
			grid[row][col] = num;
		
			if (solvingSudoku(grid, row, col + 1))
				return true;
		}
	
		grid[row][col] = 0;
	}
	return false;
}
int main()
{
	// 0 means unassigned cells
	int grid[H][H] = { { 3, 0, 6, 5, 0, 8, 4, 0, 0 },
					{ 5, 2, 0, 0, 0, 0, 0, 0, 0 },
					{ 0, 8, 7, 0, 0, 0, 0, 3, 1 },
					{ 0, 0, 3, 0, 1, 0, 0, 8, 0 },
					{ 9, 0, 0, 8, 6, 3, 0, 0, 5 },
					{ 0, 5, 0, 0, 9, 0, 6, 0, 0 },
					{ 1, 3, 0, 0, 0, 0, 2, 5, 0 },
					{ 0, 0, 0, 0, 0, 0, 0, 7, 4 },
					{ 0, 0, 5, 2, 0, 6, 3, 0, 0 } };

	if (solvingSudoku(grid, 0, 0))
		print(grid);
	else
		cout << "SODUKO SOLUTION IS NOT FOUND " << endl;

	return 0;
}
