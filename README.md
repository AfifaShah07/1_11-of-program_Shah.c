#include <stdio.h>
#include <ctype.h>

#define MAX 100

int stack[MAX];
int top = -1;

void push(int x) {
    stack[++top] = x;
}

int pop() {
    return stack[top--];
}

int main() {
    char exp[MAX];
    char *e;
    int num, op1, op2;

    printf("Enter a postfix expression: ");
    scanf("%s", exp);

    e = exp;

    while (*e != '\0') {
        if (isdigit(*e)) {
            // convert char digit to int
            num = *e - '0';
            push(num);
        }
        else {
            op2 = pop();
            op1 = pop();

            switch (*e) {
                case '+': push(op1 + op2); break;
                case '-': push(op1 - op2); break;
                case '*': push(op1 * op2); break;
                case '/': push(op1 / op2); break;
            }
        }
        e++;
    }

    printf("Result = %d\n", pop());
    return 0;
}# 1_11-of-program_Shah.c
Arithmetic expression evaluation using stack
