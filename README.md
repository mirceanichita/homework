# homework
#include<iostream>
#include<string>
using namespace std;
int ninputs;
int vf(char, int); //declararea functiei
int **afd;
char * c;
int main(){
    int nstari, nfinale;
    char a;
    int s , final_a , v;
    string string_a;
    cout << "Nr stari:" ;
    cin >> nstari;
    cout << "Nr simboluri:" ;
    cin >> ninputs;
    c = new char [nstari];
    afd= new int *[ninputs];
    for(int i = 0; i < ninputs; ++i){
        afd[i] = new int[nstari];
    }
    cout << "Simboluri:" << endl;
    for(int i = 0 ;i < ninputs ;i++){
        cout << "simbol " << i+1<< " ";
        cin >> c[i];
    }
    cout << "Nr stari finale";
    cin >> nfinale;
    if(nfinale > nstari){
        cout << "EROR" << endl;
        return 1;
    }
    int *f = new int [nfinale];
    for(int i = 0 ;i < nfinale ;i++){
        cout << "Stare finala " << i+1 << " : q";
        cin >> f[i];
    }
       cout << "(stare initiala, simbol ) = starea urmatoare";

    for(int i = 0 ;i < ninputs ;i++){
        for(int j=0 ;j < nstari ;j++){
            cout << "\n(q" << j  << " , " << c[i] << ") = q";
            cin >>afd[i][j];
        }
    }
    do{
        final_a = 0;
        v = 0;
        s = 0;
        cout << "Insereaza cuvantul";
        cin >> string_a;
        while(string_a[v]!='\0'){
            if((s = vf(string_a[v++] , s)) < 0){
                break;
            }
        }
        for(int i = 0 ;i < nfinale ;i++){
            if(s == f[i]){
                final_a = 1;
            }
        }
        if(final_a == 1){
            cout << endl << "valid" << endl << endl;
        }else{
            cout << endl << "invalid" << endl << endl;
        }
        cout << "Continuati?(y/n) ";
        cin >> a;
    }while(a == 'y');
    for(int i = 0; i < ninputs; i++){
            delete []afd[i];
    }
    delete []afd;
    delete []c;

    return 0;
}
int vf(char b, int d){
    for(int j = 0 ;j < ninputs ;j++){
        if(b == c[j])
            return(afd[j][d]);
    }
    return -1;
}

