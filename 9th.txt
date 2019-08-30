#include<iostream>
#include<cmath>
using namespace std;
struct bst{
    int data;
    bst *left;
    bst *right;
};
bst* insert(bst *root, int x){
    if(root==0){
        bst *root=new bst();
        root->data=x;
        root->left=root->right=0;
        return root;
    }
    if(x<=root->data)
    root->left=insert(root->left,x);
    else if(x>root->data)
    root->right=insert(root->right,x);
    return root;
}
int max_kill(bst *root){
    if(root==0)
    return -1;
    return max(max_kill(root->left),max_kill(root->right))+1;
}
int main(){
    int t,n,x;
    cin>>t;
    for(int j=1; j<=t; j++){
    cin>>n;
      bst *root=0;
    for(int i=1; i<=n; i++){
        cin>>x;
        root=insert(root,x);
    }
    int result=max_kill(root)+1;
    if(result==-1)
    cout<<"0";
    else
    cout<<result;
    cout<<endl;
    }
    return 0;
}