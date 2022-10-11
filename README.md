# Paranthesis-Matching
Paranthesis Matching Problem
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

struct Stack{

int top;

int size;

char* arr;

};

void Push(struct Stack* sp,char n){

sp->top++;

sp->arr[sp->top]=n;

}

char Pop(struct Stack* sp){

sp->top--;

return sp->arr[sp->top];

}

int match(char a,char b){

if(a=='(' && b==')'){

return 1;

}

else if(a=='{' && b=='}'){

return 1;

}

else if(a=='[' && b==']'){

return 1;

}

return 0;

}

int ParanthesisMatching(char * exp){

    // Create and initialize the stack

    struct Stack* sp=(struct Stack*)malloc(sizeof(struct Stack));

    sp->size = 100;

    sp->top = -1;

    sp->arr = (char *)malloc(sp->size * sizeof(char));

    char popped_ch;

 

    for (int i = 0; exp[i]!='\0'; i++)

    {

        if(exp[i]=='(' || exp[i]=='{' || exp[i]=='['){

            Push(sp, exp[i]);

        }

        else if(exp[i]==')'|| exp[i]=='}' || exp[i]==']'){

            if(sp->top==-1){

                return 0;

            }

            popped_ch =sp->arr[sp->top];

            if(!match(popped_ch, exp[i])){ 

              return 0;  

            }

            Pop(sp);

        }

    }

 

    if(sp->top==-1){

        return 1;

    }

    else{

        return 0;

    }

}

int main(){

char hunny[19];

printf("Enter a char");

scanf("%s",&hunny);

getchar();

if(ParanthesisMatching(hunny)){

printf("matching");

}

else{

printf("not matching");

}

}

 
