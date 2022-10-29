#include <stdio.h>
#include <string.h>

int main(){

    char r[50], dvd[100], dvs[50], code[100];
    int dvdlen, dvslen, i;

    printf("Dividend: ");
    scanf("%s", dvd);
    printf("Divisor: ");
    scanf("%s", dvs);

    dvdlen = strlen(dvd);
    dvslen = strlen(dvs);
    dvd[dvslen] = '\0';
    r[dvslen] = '\0';

    strcpy(code, dvd);
    for(i = 0; i < dvslen - 1; i++){
        code[dvdlen + i] = '0';
    }

    for(int j = 0; j < dvdlen; j++){
        if(code[j] != '0'){
            for(int k = 0; k < dvslen; k++){
                r[k] = code[j + k] = (code[j + k] == dvs[k]) ? '0' : '1';
            }
        }
    }
    printf("\nCRC: %s\n", r);

    for(int i = 0; i < dvslen; i++){
        r[i] = r[i+1];
    }

    printf("Data Transmitted: %s", strcat(dvd, r));

    return 0;
}