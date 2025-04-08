# -自己写的输入模板（判断输入是否回文），输入合法性判断 - #

#include<iostream>
#include<String>
#include<stdexcept>
#include<cmath>
using namespace std;

bool isPalindrome(const string s ) {
	int left = 0;
	int right = s.length() - 1;
	while (left < right) {
		if (s[left] != s[right]) {
			return false;
		}
		left++;
		right--;
	}
	return true;
}

int main() {
	while (true) {

		string input;
		cout << "请输入一个整数以判断是否是回文数（按q退出）：";
		getline(cin,input);
		if (input == "q" || input == "Q") {
			cout << "程序结束！" << endl;
			break;
		}
		try {
			size_t pos;
			int number = stoi(input, &pos);
			string numstr = to_string(abs(number));
			if (pos != input.length()) {
             throw invalid_argument("Invalid input");
			}

			if (isPalindrome(input)) {
				cout << number << "是回文数" << endl;
			}
			else {
				cout << number << "不是回文数" << endl;
			}
			
		}
		catch (const invalid_argument& e) {
			cout<<"请输入一个整数！"<<endl;
		}
		catch (const out_of_range& e) {
			cout << "输入的整数超出范围！" << endl;
		}
		catch (const exception& e) {
			cout << "发生了一个错误：" << e.what() << endl;
		}

	}
}
