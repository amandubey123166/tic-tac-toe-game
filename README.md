# tic-tac-toe-game
now basic than upgrade with timer
#include<iostream>
#include<vector>
using namespace std;
class game{
	vector<vector<char>> arr={{'1','2','3'},{'4','5','6'},{'7','8','9'}};
	int count=0;
	public:
	void box();
	void input();
	void choose(char,int);
	int winer();
};

void game::box(){
	 cout << "\n";
    for (int i = 0; i < 3; i++) {
        cout << " " << arr[i][0] << " | " << arr[i][1] << " | " << arr[i][2] << " \n";
        if (i < 2) cout << "---|---|---\n";
    }
    cout << "\n";
}
void game::input(){
//	int count=0;
		int decide=1;
	while(count<9){
	
		   int decide = 1;
    while (count < 9) {
        char choice;
        if (decide == 1) {
            cout << "Player 1\nEnter your indexing number: ";
        } else {
            cout << "Player 2\nEnter your indexing number: ";
        }
        cin >> choice;
        choose(choice, decide);
        box();
        count++;

        int winner = winer();
        if (winner == 1) {
            cout << "Congratulations! Player 1 wins.\n";
            return;
        }
        if (winner == 2) {
            cout << "Congratulations! Player 2 wins.\n";
            return;
        }
        
        decide = (decide == 1) ? 2 : 1;  // टर्न स्विच करना
    }
    cout << "Match is draw.\n";
	
//	box();
}
}
void game::choose(char s,int x){
    while (true) {  // जब तक valid move नहीं मिलती, तब तक input दोबारा माँगेगा
        bool validMove = false;
        for (int k = 0; k < 3; k++) {
            for (int l = 0; l < 3; l++) {
                if (s == arr[k][l]) { // सही move check
                    arr[k][l] = (x == 1) ? 'X' : 'O';
                    validMove = true;
                    return;  // सही move मिली, तो function से return कर दो
                }
            }
        }
        if (!validMove) {
            cout << "Invalid move! Try again: ";
            cin >> s;  // गलत move पर input दोबारा लो
        }
    }
//	return choice;
}

int game::winer(){
	for(int k=0;k<3;k++){
	if(arr[k][0]==arr[k][1] && arr[k][1]==arr[k][2]){
		if(arr[k][0]=='X'){
			return 1;
		}else{
		return 2;
	}
	}
	if(arr[0][k]==arr[1][k] && arr[1][k]==arr[2][k]){
			if(arr[0][k]=='X'){
			return 1;
		}else{
		return 2;
	}
	}
}
	if(arr[0][0]==arr[1][1] && arr[1][1]==arr[2][2]){
			if(arr[0][0]=='X'){
			return 1;
		}else{
		return 2;
	}
	}
	if(arr[0][2]==arr[1][1] && arr[1][1]==arr[2][0]){
			if(arr[0][2]=='X'){
			return 1;
		}else{
		return 2;
	}
	}
	return 0;
}
int main(){
	game g;
	g.box();
	g.input();
	return 0;
}
