//Project: Project 8 The Tic-Tac-Toe Game
//Author: Nora Elattar
//Date: 4/24/17
#include<iostream>
using namespace std;

class Board {
	char** bd;
	char** Create2DArray(int r, int c);
	void Destroy2DArray(char** arr);

public:
	static int nec;     //nec: number of empty cells
	Board(int dim = 3);
	~Board(){};
	void display();
	int size;
	friend class Player;
};
int Board::nec = 9; //initialized nec to 9 outside of class def
Board::Board(int dim){
	size = dim;
	bd = Create2DArray(dim, dim);
}
char** Board::Create2DArray(int r, int c){ //Creates 2D array
	char **A = new char*[r];
	for (int i = 0; i < r; i++){
		A[i] = new char[c];
		for (int j = 0; j < c; j++)
			A[i][j] = ' '; //sets all the values in the array to 0
	}
	return A;
}
void Board::Destroy2DArray(char** arr){ //destroys 2D array
	for (int i = 0; i < size; i++)
		delete[] arr[i];
	delete[] arr;
}
void Board::display(){ //prints out the display
	for (int i = 0; i < size; i++){
		for (int j = 0; j < size; j++){
			cout << " [ " << bd[i][j] << " ]";
		}
		cout << endl;
	}
}
class Player{
	char pn; //players name

public:
	Player(char ch = ' ') { pn = ch; }
	~Player() { }
	bool move(int row, int col, Board& b);
	bool doIWin(int row, int col, Board& b);
	void setName(char c) { pn = c; }
	char getName() const { return pn; }
};
bool Player::move(int row, int col, Board& b)
{
	if (row <= 3 && col <= 3 && row > 0 && col > 0 && b.bd[row - 1][col - 1] == ' '){ //performs move if true
		b.bd[row - 1][col - 1] = pn;
		b.nec -= 1;
		return true;
	}
	return false;

	//b[row][col]
	//check if its vaid and if it is a space or not
}
bool Player::doIWin(int row, int col, Board& b){
	//check if the player wins
	// if the columns are equals or the rows are equal. or if the colums and rows equal each other (for diaganol win)
	for (int i = 0; i < b.size; i++)
		for (int j = 0; j < b.size; j++)
		{
			if (b.bd[0][j] == pn && b.bd[0][j] == b.bd[1][j] && b.bd [0][j] == b.bd[2][j] ||
				b.bd[i][0] == pn && b.bd[i][0] == b.bd[i][1] && b.bd[i][0] == b.bd[i][2] ||
				b.bd[0][0] == pn && b.bd[0][0] == b.bd[1][1] && b.bd[0][0] == b.bd [2][2] ||
				b.bd[0][2] == pn && b.bd[0][2] == b.bd[1][1] && b.bd [1][1] == b.bd[2][0] )
				return true;
		}
	return false;
}
int main()
{
	Board b; //calls default constructor for board
	Player p1, p2; //calls default constructor for player
	int row = 0; //sets row to 0
	int col = 0; //sets col to 0
	char n1;
	cout << "There are two players X and O, who moves first?" << endl; //prints out instructions for user
	cout << "Type in 'x' or 'X', X will move first, anything else O moves first: ";
	cin >> n1; //prompts user for name
	if (n1 == 'x')
		n1 = 'X';
	if (n1 == 'X'){
		p2.setName('O'); //sets the name of the user depending on input
		p1.setName(n1);
	}
	else{
		p1.setName('O');
		p2.setName('X');
	}
	cout << "Initial Board: " << endl;
	b.display(); //prints out initial board
	while (true) //while loop for the players to keep playing until someone wins or both draw
	{
		cout << p1.getName() << ", your turn to move. Enter the row and col: ";
		cin >> row >> col;
		if (!p1.move(row, col, b)){
			cout << "Invalid move. Try again." << endl;
			continue;
		}
		b.display();
		if (p1.doIWin(row, col, b)){
			cout << p1.getName() << " wins!!" << endl;
			break;
		}
		
		cout << p2.getName() << ", your turn to move. Enter the row and col: ";
		cin >> row >> col;
		if (!p2.move(row, col, b)){
			cout << "Invalid move. Try again." << endl;
			continue;
		}
		b.display();
		if (p2.doIWin(row, col, b)){
			cout << p2.getName() << " wins!!" << endl;
			break;
		}
	}
	if (!p1.doIWin(row, col, b) && !p2.doIWin(row, col, b)){
		cout << "Nobody wins: draw." << endl; //prints if no one wins
	}
	cout << "The remaining spaces are: " << b.nec << endl; //prints the remaining spaces on the board
	

}
