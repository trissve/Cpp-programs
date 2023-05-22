

#include <iostream>
using namespace std;


void Cardinality(int set[], int* power) {

    int flag = 0, i = 0;

    while(flag == 0){
        if(set[i] == -1) {
            flag = 1;
        }
        i++;
    }

    *power = (i - 1);
}


void extraAdd(int x, int set[]){

    int n;   //ilosc elemetow
    int flag = 1;
    Cardinality(set, &n);

    for(int i = 0; i < n; i++){
        if(set[i] == x){
            flag = 0;
        }
    }

    if(x < 1 || x > 4095){
        flag = 0;
    }

    if(flag == 1){
        set[n] = x;
        set[n + 1] = -1;
    }

}


void BubbleSort(int set[], int N)
{
    for(int i = 0; i < N - 1; i++)
        for(int j = 0; j < N - i - 1; j++)
            if(set[j] > set[j + 1])
                swap(set[j], set[j + 1]);       // zamiana
}


void Add(int x, int set[]){

    int n;   //ilosc elemetow
    int flag = 1;
    Cardinality(set, &n);

    for(int i = 0; i < n; i++){
        if(set[i] == x){
            flag = 0;
        }
    }

    if(x < 1 || x > 4095){
        flag = 0;
    }


    if(flag == 1){
        set[n] = x;
        set[n + 1] = -1;
        BubbleSort(set, n + 1);
    }
    else{
        BubbleSort(set, n);
    }


}

bool Element(int x, int set[]){

    int n;
    Cardinality(set, &n);

    for(int i = 0; i < n; i++){
        if(set[i] == x){
            return true;
        }
    }
    return false;
}


void Create(int n, int tab1[], int tab2[]) {

    int j = 0;

    for(int i = 0; i < n; i++) {
        if(tab1[i] > 0 && tab1[i] < 4096){
            if(!Element(tab1[i], tab2)){
                tab2[j] = tab1[i];
                j++;
            }
        }
    }

    tab2[j] = -1;

    BubbleSort(tab2, j);

}


void Intersection(int set1[], int set2[], int output[]) {

    int n1, j = 0;
    output[0] = -1;
    Cardinality(set1, &n1);

    for(int i = 0; i < n1; i++){
        if(Element(set1[i], set2)){
            extraAdd(set1[i], output);
            j++;
        }
    }

    j--;
    BubbleSort(output, j);
}


void Difference(int set1[], int set2[], int output[]){

    int n1, j = 0;
    output[0] = -1;
    Cardinality(set1, &n1);

    for(int i = 0; i < n1; i++){
        if(!Element(set1[i], set2)){
            extraAdd(set1[i], output);
            j++;
        }
    }

    j--;
    BubbleSort(output, j);

}


void Symmetric(int set1[], int set2[], int output[]){

    int n1, n2, j = 0;
    output[0] = -1;
    Cardinality(set1, &n1);
    Cardinality(set2, &n2);

    for(int i = 0; i < n1; i++){
        if(!Element(set1[i], set2)){
            extraAdd(set1[i], output);
            j++;
        }
    }

    for(int i = 0; i < n2; i++){
        if(!Element(set2[i], set1)){
            extraAdd(set2[i], output);
            j++;
        }
    }

    BubbleSort(output, j);

}


void Union(int set1[], int set2[], int sum[]){

    int n1, n2, j = 0;
    //najpierw robie sobie czesc wspolna
    Cardinality(set1, &n1);
    Cardinality(set2, &n2);

    sum[0] = -1;

    for(int i = 0; i < n1; i++){
        if(Element(set1[i], set2)){
            extraAdd(set1[i], sum);
            j++;
        }
        else{
            extraAdd(set1[i], sum);
            j++;
        }
    }


    for(int i = 0; i < n2; i++){
        if(!Element(set2[i], set1)){
            extraAdd(set2[i], sum);
            j++;
        }
    }

    BubbleSort(sum, j);

}


void Complement(int set1[], int set2[]){

    set2[0] = -1;
    int j = 0;

    for(int i = 1; i < 4096; i++){
        if(!Element(i, set1)){
            extraAdd(i, set2);
            j++;
        }
    }

    j--;
    BubbleSort(set2, j);

}


bool Subset(int set1[], int set2[]){

    int n1;
    Cardinality(set1, &n1);

    for(int i = 0; i < n1; i++){
        if(!Element(set1[i], set2)){
            return false;
        }
    }

    return true;
}


bool Equal(int set1[], int set2[]) {

    int n1, n2;
    Cardinality(set1, &n1);
    Cardinality(set2, &n2);

    if (n1 != n2) {
        return false;
    }

    for(int i = 0; i < n1; i++){
        if(!Element(set1[i], set2)){
            return false;
        }
    }

    return true;

}


bool Empty(int set[]){

    if(set[0] == -1){
        return true;
    }
    return false;
}


bool Nonempty(int set[]){

    if(set[0] == -1){
        return false;
    }
    return true;
}


double Arithmetic(int set[]){

    int n, sum = 0;
    Cardinality(set, &n);

    if(n == 0){
        return 0;
    }

    for(int i = 0; i < n; i++){
        sum += set[i];
    }

    double av;

    av = (double)sum/(double)n;

    return av;
}


double Harmonic(int set[]){

    int n;
    double sum = 0;
    Cardinality(set, &n);

    if(n == 0){
        return 1;
    }

    for(int i = 0; i < n; i++){
        sum += (1/(double)set[i]);
    }

    double av;

    av = (double)n/sum;

    return av;


}


void MinMax(int set[], int* min, int &max){

    int n;
    Cardinality(set, &n);
    int temp_min = 4096, temp_max = 0;

    if(n != 0){
        for(int i = 0; i < n; i++){
            if(set[i] < temp_min){
                temp_min = set[i];
            }
            if(set[i] > temp_max){
                temp_max = set[i];
            }
        }
        *min = temp_min;
        max = temp_max;
    }
}


int char_len(char tab[]){

    int i = 0;
    int flag = 0;

    while(flag == 0){
        if(tab[i] == 'a' || tab[i] == 'h' || tab[i] == 'm' || tab[i] == 'c'){
            i++;
        }
        else{
            flag = 1;
        }

    }


    return i;

}


bool if_in(char tab[], char x){

    int n;
    n = char_len(tab);

    for(int i = 0; i < n; i++){
        if(tab[i] == x){
            return true;
        }
    }
    return false;
}


void Properties(int set[], char op[], double &a, double* h, int &min, int* max, int &c){

    if(if_in(op, 'a')){
        a = Arithmetic(set);
    }

    if(if_in(op, 'h')){
        *h = Harmonic(set);
    }

    if(if_in(op, 'm')){
        MinMax(set, &min, *max);
    }

    if(if_in(op, 'c')){
        Cardinality(set, &c);
    }




}
