# interviewbit---array---rotate-matrix

**-----> Question:**

You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

You need to do this in place.

Note that if you end up using an additional array, you will only receive partial score.

Example:

If the array is

[
    [1, 2],
    [3, 4]
]
Then the rotated array becomes:

[
    [3, 1],
    [4, 2]
]



**------> Code (my own code):**

void Solution::rotate(vector<vector<int> > &v) {

    int n=v.size(),dir=0,t=0,b=n-1,l=0,r=n-1,x=n;

    while(t<b && l<r){
        for(int j=1;j<x;j++){
            int a=v[t][l];
            if(dir==0){
                for(int i=t;i<b;i++){
                    v[i][l]=v[i+1][l];
                }
                dir=1;
            }
            if(dir==1){
                for(int i=l;i<r;i++){
                    v[b][i]=v[b][i+1];
                }
                dir=2;
            }
            if(dir==2){
                for(int i=b;i>t;i--){
                    v[i][r]=v[i-1][r];
                }
                dir=3;
            }
            if(dir==3){
                for(int i=r;i>l+1;i--){
                    v[t][i]=v[t][i-1];
                }
                dir=0;
            }

            v[t][l+1]=a;
        }

        t++;
        l++;
        b--;
        r--;
        x=x-2;
    }
}
  
  
  
  **------> Code (short- transpose method):**
  
  void Solution::rotate(vector<vector<int> > &v) {

    int n=v.size();

    for(int i=0;i<n;i++){
        for(int j=i;j<n;j++){
            swap(v[i][j],v[j][i]);
        }
    }

    for(int i=0;i<n;i++){
        for(int j=0;j<n/2;j++){
            swap(v[i][j],v[i][n-j-1]);
        }
    }
    
    
}

