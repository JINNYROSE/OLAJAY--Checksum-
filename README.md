// C++ implementation of the above approach
#include <bits/stdc++.h>
using namespace std;
 
// Function to find the One's complement
// of the given binary string
string Ones_complement(string data)
{
    for (int i = 0; i < data.length(); i++) {
        if (data[i] == '0')
            data[i] = '1';
        else
            data[i] = '0';
    }
 
    return data;
}
 
// Function to return the checksum value of
// the give string when divided in K size blocks
string checkSum(string data, int block_size)
{
    // Check data size is divisible by block_size
    // Otherwise add '0' front of the data
    int n = data.length();
    if (n % block_size != 0) {
        int pad_size = block_size - (n % block_size);
        for (int i = 0; i < pad_size; i++) {
            data = '0' + data;
        }
    }
 
    // Binary addition of all blocks with carry
    string result = "";
