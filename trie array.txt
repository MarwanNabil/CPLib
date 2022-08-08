#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <memory.h>
#include <limits.h>
#include <math.h>
#include <string.h>
#include <string>
#include <cstring>
#include <algorithm>
#include <vector>
#include <queue>
#include <stack>
#include <set>
#include <map>
#include <unordered_set>
#include <unordered_map>
using namespace std;
vector<vector<int> > v;
vector<bool> e;
void insert(string &s) {
	int cur = 0;
	for (int i = 0; i < s.size(); ++i) {
		char c = s[i] - 'a';
		if (v[cur][c] == -1) {
			v[cur][c] = v.size();
			v.push_back(vector<int>(26, -1));
			e.push_back(false);
		}
		cur = v[cur][c];
	}
	e[cur] = true;
}
bool find(string &s) {
	int cur = 0;
	for (int i = 0; i < s.size(); ++i) {
		char c = s[i] - 'a';
		if (v[cur][c] == -1) {
			return false;
		}
		cur = v[cur][c];
	}
	return e[cur];
}
int main() {
	int n;
	cin >> n;
	v.resize(1);
	v[0].resize(26, -1);
	e.push_back(false);
	for (int i = 0; i < n; ++i) {
		string s;
		cin >> s;
		insert(s);
	}
	int q;
	cin >> q;
	for (int i = 0; i < q; ++i) {
		string s;
		cin >> s;
		if (find(s))
			cout << "Yes" << endl;
		else
			cout << "No" << endl;
	}
	return 0;
}