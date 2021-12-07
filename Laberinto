//
//  main.c
//  Laberinto
//
//  Created by Angel Montillo on 04/12/21.
//

#include <stdio.h>
#include<stdio.h>
#include<stdlib.h>
#include<time.h>
#include<math.h>

int tamanho,i,j,k,labFinali,labFinalj,n=0,m=0;
char **matrizLaberinto;
/*
               0   1   2   3   4   5   6   7   8   9   10
               ╣   ║   ╗   ╝   ╚   ╔   ╩   ╦   ╠   ═    ╬
*/
int piezas[]={185,186,187,188,200,201,202,203,204,205,206};

//Funcion para limpiar la consola
void limpia(){
    system("@cls||clear");
}

//Funcion para ingresar el valor de n(tamanho)
void ingresaValor(){
    while(tamanho<7){
    limpia();
    printf("%c",piezas[5]);
    for(i=0;i<23;i++) printf("%c",piezas[9]);
    printf("%c\n",piezas[2]);
    printf("%c Ingresa el valor de n %c\n",piezas[1],piezas[1]);
    printf("%c",piezas[4]);
    for(i=0;i<23;i++) printf("%c",piezas[9]);
    printf("%c\n\n\n",piezas[3]);
    scanf("%d",&tamanho);
    tamanho+=2;
    }
}
void rellenaBordes(){
    //Se ingresa el valor de n para el tamanho del laberinto
    ingresaValor();

    //Se limpia la consola
    limpia();
    //Se genera una matriz global por medio de punteros
    matrizLaberinto =(int**) malloc(tamanho*sizeof(char *));
    for(i=0;i<tamanho;i++){
        matrizLaberinto[i] = (int*) malloc(tamanho*sizeof(int));
    }
    //Se crean los bordes del laberinto en la matriz
    for(i=0;i<tamanho;i++){
            matrizLaberinto[i][0] = piezas[1];
            matrizLaberinto[0][i] = piezas[9];
            matrizLaberinto[i][tamanho-1] = piezas[1];
            matrizLaberinto[tamanho-1][i] = piezas[9];
    }
    //Se crea la entrada al laberinto
    matrizLaberinto[0][0] = '+';
    matrizLaberinto[0][1] = ' ';

    //Se ponen los bordes faltantes del laberinto
    matrizLaberinto[tamanho-1][tamanho-1] = piezas[3];
    matrizLaberinto[0][tamanho-1] = piezas[2];
    matrizLaberinto[tamanho-1][0] = piezas[4];

    /*
    Se anhade una rejilla para tomar como base al hacer el laberinto
    */
    for(i=1;i<tamanho-1;i++){
        for(j=1;j<tamanho-1;j++){
                matrizLaberinto[i][j]='.';
        }
    }
}
//Genera un camino aleatorio a una salida del laberinto y crea paredes
void generaLaberinto(){
    i=1,j=1;
    srand(time(NULL));
    while(!(i==tamanho-1 || j==tamanho-1)){
        matrizLaberinto[i][j] = ' ';
        int random = rand()%4+1;
        if(random==1) i++;
        else if(random==2)j++;
        else if(random==3 && i>1)i--;
        else if(random==4 && j>1)j--;
    }
    matrizLaberinto[i][j]=' ';
    labFinali=i,labFinalj=j;
    //Genera algunos huecos en las paredes
    srand(time(NULL));
    for(i=1;i<tamanho-1;i++){
        for(j=1;j<tamanho-1;j++){
            if(matrizLaberinto[i][j]=='.'){
                int r = rand()%11+1;
                if(r==2 || r==5 || r==11) matrizLaberinto[i][j] = ' ';
            }
        }
    }
    //Genera las paredes del laberinto
    srand(time(NULL));
    for(i=1;i<tamanho;i++){
        for(j=1;j<tamanho;j++){
            if(matrizLaberinto[i][j]=='.'){
                int r = rand()%11;
                matrizLaberinto[i][j]=piezas[r];
            }
        }
    }
}
void imprimeLaberinto(){
    limpia();
    for(i=0;i<tamanho;i++){
        for(j=0;j<tamanho;j++){
            printf("%c",matrizLaberinto[i][j]);
        }
        printf("\n");
    }
}
void imprimeReglas(){
    printf("\n\nPara ir a la izquierda escribe: 4\n");
    printf("Para ir a la derecha escribe: 6\n");
    printf("Para ir a la arriba escribe: 8\n");
    printf("Para ir a la abajo escribe: 2\n\n");
    printf("%c",piezas[5]);
    for(k=0;k<5;k++){
        printf("%c",piezas[9]);
    }
    printf("%c\n",piezas[2]);
    printf("%c  8  %c\n",piezas[1],piezas[1]);
    printf("%c 4 6 %c\n",piezas[1],piezas[1]);
    printf("%c  2  %c\n",piezas[1],piezas[1]);
    printf("%c",piezas[4]);
    for(k=0;k<5;k++){
        printf("%c",piezas[9]);
    }
    printf("%c\n\n",piezas[3]);
    printf("Ingresa el valor: ");
}
//Funcion que comprueba que el juego ha terminado
void comprueba(n,m){
    if(n== labFinali && m== labFinalj){
        limpia();
        printf("\n\n\t%cFelicidades llegaste al final del laberinto!\n\n\n",173);
        exit(-1);
    }
}

//Funcion que da los movimientos al juego por medio de un numero del numpad
int juega(mov){
    char x;
    if(mov==8){
            if(n>=0 && !(n-1<0) && matrizLaberinto[n-1][m]==' '){
                matrizLaberinto[n][m] = ' ';
                n--;
                matrizLaberinto[n][m] = '+';
                comprueba(n,m);
            }
    }else if(mov==4){
            if(m>=0 &&!(m-1<0) &&  matrizLaberinto[n][m-1]==' '){
                matrizLaberinto[n][m] = ' ';
                m--;
                matrizLaberinto[n][m] = '+';
                comprueba(n,m);
            }
    }else if(mov==2){
            if(n>=0 && matrizLaberinto[n+1][m]==' '){
                matrizLaberinto[n][m] = ' ';
                n++;
                matrizLaberinto[n][m] = '+';
                comprueba(n,m);
            }
    }else if(mov==6){
            if(j>=0 && matrizLaberinto[n][m+1]==' '){
                matrizLaberinto[n][m] = ' ';
                m++;
                matrizLaberinto[n][m] = '+';
                comprueba(n,m);
            }
    }else{
        printf("Esa no es una tecla correcta.\nIngresa cualquier letra para continuar: ");
        scanf("%c",&x);
    }
    return 1;
}

int main(){
    rellenaBordes();
    generaLaberinto();
    int bandera = 0;
    while(bandera==0){
        int movimiento;
        imprimeLaberinto();
        imprimeReglas();
        scanf("%d",&movimiento);
        juega(movimiento);
    }

    return 0;
}
