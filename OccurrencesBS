// Find occurrences in an array using Binary Search
// Complexity: O(logN)

#include <iostream>
#include <sstream>
#include <vector>
using namespace std;
bool DEBUG = true;

int lowerBound(int lo, int hi, int t, vector<int> nums) {
    int mid;
    while (hi >= lo) {
        // prevent overflow
        mid = lo+(hi-lo)/2;
        // adjust mid for odd-length segment
        if ((hi+lo)&1) mid++;

        if (nums[mid] == t && (mid == 0 || nums[mid-1] < t)) return mid;
        else if (nums[mid] < t) lo = mid+1;
        else hi = mid-1;
    }
    return -1;
}

int upperBound(int lo, int hi, int t, vector<int> nums) {
    int mid;
    while (hi >= lo) {
        // prevent overflow
        mid = lo+(hi-lo)/2;
        // adjust mid for odd-length segment
        if ((hi+lo)&1) mid++;

        if (nums[mid] == t && (mid == nums.size()-1 || nums[mid+1] > t)) break;
        else if (nums[mid] < t) lo = mid+1;
        else hi = mid-1;
    }
    return mid;
}


int occurrences_bs(int target, vector<int> nums) {
    int lo, hi;
    
    lo = lowerBound(0, nums.size()-1, target, nums);
    
    // given number doesnt exist
    if (lo < 0) {
        if (DEBUG) cout << "No occurrence found" << endl;
        return 0; 
    }
    
    hi = upperBound(lo, nums.size()-1, target, nums);
    
    if (DEBUG)  
        cout << "lo: " << lo << ", hi: " << hi << endl;
    return hi-lo+1;
}

int main() {
	vector<int> nums;
	string line;
	int target, i;
	
	// sample test
	int tst = 3, arr[] = {1,1,3,3,4,4,4};
	vector<int> tstvec;
	tstvec.assign(arr, arr + sizeof(arr)/sizeof(arr[0]));
	cout << tst << endl << "[1,1,3,3,4,4,4]" << endl << occurrences_bs(tst, tstvec) << endl;

    // read inputs
    cin >> target;
    cin.ignore();
    getline(cin, line);
    istringstream ss(line);
    while (!ss.eof()) {
        if (ss >> i)
        nums.push_back(i);
    }

    cout << occurrences_bs(target, nums) << endl;

	return 0;
}
