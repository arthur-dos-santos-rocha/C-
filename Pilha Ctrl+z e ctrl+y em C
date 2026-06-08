#include <stdio.h>

#define MAX 10

typedef struct{
    int dados[MAX];
    int topo;
} Pilha;

void inicializar(Pilha *p){
    p->topo = -1;
}

int estaVazia(Pilha *p){
    return p->topo == -1;
}

int estaCheia(Pilha *p){
    return p->topo == MAX - 1;
}

void push(Pilha *p, int valor){
    if(estaCheia(p)){
        printf("Pilha cheia!\n");
        return;
    }

    p->dados[++p->topo] = valor;
}

int pop(Pilha *p){
    if(estaVazia(p)){
        return -1;
    }

    return p->dados[p->topo--];
}

void mostrar(Pilha *p){
    int i;

    if(estaVazia(p)){
        printf("Pilha vazia.\n");
        return;
    }

    for(i = 0; i <= p->topo; i++){
        printf("%d ", p->dados[i]);
    }

    printf("\n");
}

int main(){

    Pilha historico;
    Pilha lixeira;

    int opcao;
    int valor;

    inicializar(&historico);
    inicializar(&lixeira);

    while(opcao != 0){

        printf("\n===== MENU =====\n");
        printf("1 - Nova acao\n");
        printf("2 - Ctrl+Z (Desfazer)\n");
        printf("3 - Ctrl+Y (Refazer)\n");
        printf("4 - Mostrar Extrato\n");
        printf("0 - Sair\n");
        printf("Opcao: ");
        scanf("%d", &opcao);

        if(opcao == 1){

            printf("Digite um valor: ");
            scanf("%d", &valor);

            push(&historico, valor);

            inicializar(&lixeira);

        }
        else if(opcao == 2){

            if(!estaVazia(&historico)){

                valor = pop(&historico);
                push(&lixeira, valor);

                printf("Acao %d desfeita.\n", valor);
            }
            else{
                printf("Nada para desfazer.\n");
            }
        }
        else if(opcao == 3){

            if(!estaVazia(&lixeira)){

                valor = pop(&lixeira);
                push(&historico, valor);

                printf("Acao %d refeita.\n", valor);
            }
            else{
                printf("Nada para refazer.\n");
            }
        }
        else if(opcao == 4){

            printf("\nHistorico: ");
            mostrar(&historico);

            printf("Lixeira (Redo): ");
            mostrar(&lixeira);
        }
    }

    return 0;
}
