#include <stdio.h>
#include <stdlib.h>
#include <locale.h>


int main(int argc, char *argv[]) //argv[1] - input.txt, argv[2] - dict.txt, argv[3] - output.txt
{
char out[1024];
char arr [1024][1024];
char word[1024];
char a,b,c = 0;
int i = 0;
int j = 0;
int r = 0;
int k = 0;
int g = 0;
int len = 0;
int height = 0;
    FILE *finput;
    finput = fopen(argv[1], "r");

remove(argv[3]);
while (!feof(finput)){
    while ((c = fgetc(finput)) !=  EOF && c != ' ' && c != '.' && c != ',' && c != '-' && c != '\n' ){
        arr[j][i] = c;
        i++;

    };
len++;
i = 0;
j++;
};

fclose(finput);

FILE *fdict;
    fdict = fopen(argv[2], "r");

for( j = 0; j < len; j++){
while(!feof(finput)){
    if ((c = fgetc(finput)) != '\n'  && c != ' '){
        word[r] = c;
        r++;
    }
   else {
    if(strcmp(arr[j], word) == 0 ){
        memset(arr[j], 0, sizeof(arr[j]));
    }
memset(word, 0, sizeof(word));
r = 0;
}
}

fseek (fdict, 0 ,SEEK_SET);
r = 0;
while ((c = fgetc(fdict)) != '\n'  ){
    word[r] = c;
    r++;

    }
if(strcmp(arr[j], word) == 0 ){
        memset(arr[j], 0, sizeof(arr[j]));
    }
fseek (finput, 0 ,SEEK_SET);
};


while (!feof(fdict)) {
    if (c = fgetc(fdict) == '\n')
    height++;
}

for (int j = 0; j < len; j++)
for (int j = 0; j < len; j++){
    for (int i = 0; i < len; i++){
        if((strcmp(arr[j], arr[i]) == 0) & (j!=i) )
            memset(arr[j], 0, sizeof(arr[j]));
    }
}

FILE *foutput;

for (int j = 0; j < len; j++){
    if (arr[j][0] != '\0'){
        foutput = fopen(argv[3], "a+");
        fputs(arr[j], foutput);
        fputs("\n", foutput);
    }
}
foutput = fopen(argv[3], "r");
if (foutput == NULL)
    printf ("OK\n");
else printf ("WARNING\n");

fclose(finput);
fclose(fdict);
fclose(foutput);
return 0;
}
