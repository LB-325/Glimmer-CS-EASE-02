```
#include<stdio.h>
#include<stdlib.h>
#define HZ 100
typedef char in;
typedef struct stack{ 
    in data;
    struct stack *next;
}stack;

stack* init(){     //初始化 
    stack *s=(stack*)malloc(sizeof(stack));
    s->data=0;
    s->next=NULL;
    return s;
}

int judge(stack *s){          //判断是否为空栈
    if(s->next==NULL){
    printf("空的\n");
    return 1;
    }
    else{
        return 0;
    }
}

int push(stack *s,in e){       //进栈
    stack *p=(stack*)malloc(sizeof(stack));
    p->data=e;
    p->next=s->next;
    s->next=p;
    return 1;
}

int out(stack *s,in *e){       //出栈
    if(s->next==NULL){
        *e='\0';
        return 0;
    }
    stack *q=s->next;
    *e=q->data;
    s->next=q->next;
    free(q);
    return 1;
}

int gettop(stack *s,in *e){       //获取头数据
    if(s->next==NULL){
        printf("空的\n");
        return 0;
    }
    stack *i=s->next;
    *e=i->data;
    return 1;
}

int list(stack *s){
    stack *l=s;
    if(l->next==NULL){
        printf("空的\n");
        return 0;
    }
    else{
        for(;l->next!=NULL;l=l->next){
            stack *i=l->next;
            printf("%c ",i->data);
        }
    }
}

int main(){
    in e,k;
    stack *z=init();
    int i,m=1,n=0;
    do{
        m=1;
        printf("Enter the number whose position is odd number:");    //在终端输入数字串中奇数部分
        scanf("%d",&i);
        for(m=1;m<=i;m++){
            printf("Enter the character:");      //在终端输入密文串中字符
            scanf(" %c",&k);
            push(z,k);
        }
        m=1;
        n++;
        printf("Enter the number whose position is even number:");   //在终端输入数字串中偶数部分
        scanf("%d",&i);
        for(m=1;m<=i;m++){
            out(z,&e);
            printf("%c\n",e);       //输出弹出的字符
        }
        n++;
    }while(n<34);
}  
```

---

最终解密结果：g l i n m m r i h n e r a t e e k o f 4 a d r r
