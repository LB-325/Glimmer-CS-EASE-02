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
    if(s==NULL){
        printf("分配内存失败\n");
        return NULL;
    }
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
    if(p==NULL){
        printf("分配内存失败\n");
        return 0;
    }
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
    in e;
    stack *z=init();
    push(z,'k');
    push(z,'i');
    push(z,'g');     //3 J 1   （3表示数字串中第一个字符，J表示位于奇数位置，1表示序号）

    out(z,&e);       //1 O 2
    printf("%c ",e);

    push(z,'l');     //1 J 3

    out(z,&e);       //2 O 4
    printf("%c ",e);
    out(z,&e);
    printf("%c ",e);

    push(z,'n');     //1 J 5

    out(z,&e);
    printf("%c ",e); //1 O 6

    push(z,'m');     //1 j 7

    out(z,&e);       //1 O 8
    printf("%c ",e);

    push(z,'r');     //2 J 9
    push(z,'m');

    out(z,&e);       //2 O 10
    printf("%c ",e);
    out(z,&e);
    printf("%c ",e);

    push(z,'e');     //2 J 11
    push(z,'i');

    out(z,&e);       //1 O 12
    printf("%c ",e);

    push(z,'a');     //2 J 13 
    push(z,'h');

    out(z,&e);       //1 O 14
    printf("%c ",e);

    push(z,'e');     //2 J 15
    push(z,'n');  

    out(z,&e);       //2 O 16
    printf("%c ",e);
    out(z,&e);
    printf("%c ",e);

    push(z,'r');     //1 J 17

    out(z,&e);       //2 O 18
    printf("%c ",e);
    out(z,&e);
    printf("%c ",e);

    push(z,'t');     //1 J 19

    out(z,&e);       //2 O 20
    printf("%c ",e);
    out(z,&e);
    printf("%c ",e);

    push(z,'e');     //1 J 21

    out(z,&e);       //2 O 22 
    printf("%c ",e);
    out(z,&e);
    printf("%c ",e);

    push(z,'o');     //1 J 23

    out(z,&e);       //1 O 24
    printf("%c ",e);

    push(z,'f');     //1 J 25

    out(z,&e);       //2 O 26
    printf("%c ",e);
    out(z,&e);   
    printf("%c",e);

    push(z,'4');     //1 J 27

    out(z,&e);       //1 O 28 
    printf("%c ",e);

    push(z,'a');     //1 J 29

    out(z,&e);       //1 O 30
    printf("%c ",e);

    push(z,'r');     //2 J 31
    push(z,'d');

    out(z,&e);       //2 O 32
    printf("%c ",e);
    out(z,&e);   
    printf("%c ",e);

    push(z,'a');     //2 J 33
    push(z,'r');

    out(z,&e);       //1 O 34  
    printf("%c ",e);

}
```

---

解密最终结果：g l i n m m r i h n e r a t e e k o f 4 a d r r
