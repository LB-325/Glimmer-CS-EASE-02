```
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<stdbool.h>
typedef int in;     //方便修改数据类型
typedef struct li{
    in data;
    struct li *next;
}li;

li* init(){       //初始化
    li *h=(li*)malloc(sizeof(li));  //函数分配内存
    h->data=1;
    h->next=NULL;
    return h;
}

void H(li *l,in e){       //头插法，在头数据后插入一个新数据，*l是第一个数据，e是插入的数据元素
    li *p=(li*)malloc(sizeof(li));
    p->data=e;
    p->next=l->next;
    l->next=p;
}

li* getl(li *l){    //得到尾节点地址
    li *p=l;
    while(p->next!=NULL){
        p=p->next;
    }
    return p;
}

li* T(li *l,in e){     //尾插法，在链表最后插入数据
    li *tail;
    li *o=l;
    tail=getl(o);
    li *p=(li*)malloc(sizeof(li));
    p->data=e;
    tail->next=p;
    p->next=NULL;
    return p;
}

void list(li *l){        //遍历，将链表中数据全部输出一次
    li *p=l;
    while(p!=NULL){
        printf("%d\n",p->data);
        p=p->next;
    }
    printf("\n");
}

int D(li *l,int LOCATION){     //删除数据，删除第LOCATION个节点数据
    li *p=l;
    int i=1;
    while(i<LOCATION-1){
        p=p->next;
        i++;
        if(p==NULL){
            return 0;
        }
    }

    if(p==NULL||LOCATION<1){
        printf("所删除的位置信息错误\n");
        return 0;
    }
    li *q;
    q=p->next;
    p->next=q->next;
    free(q);      //释放内存
}


int main(){
    li *circle=init();
  

    printf("Enter the operation that you choose(T,H,D,C), C to end:");
    char a,t='T',d='D',h='H',c='C';
    scanf("%c",&a);
    do{

        if(a==t){    //操作T，输入待操作的三个数
            int m,n,e;
  
            scanf("%d",&m);

            scanf("%d",&n);   

            scanf("%d",&e);
            T(circle,m);
            T(circle,n);
            T(circle,e);
   

        }else{
            if(a==h){       //操作H，输入待操作的三个数
            int m,n,e;

            scanf("%d",&m);

            scanf("%d",&n);   

            scanf("%d",&e);
            H(circle,m);
            H(circle,n);
            H(circle,e);
   
            }else{
                if(a==d){    //操作D，输入待操作的1个数
                    int b;

                    scanf("%d",&b);
                    D(circle,b);
  
                }else{
                    if(a==c){     //操作C，结束操作
                        break;
                    }else{
                    printf("Please enter the right operation\n");
  
                    }
                }
            }
        }
        printf("Enter the operation that you choose(T,H,D,C), C to end:");
        scanf(" %c",&a);

    }while(a!='C');
    li *pos=getl(circle);
    pos->next=circle;         //转化为环状链表
    li *bl=circle->next;
    printf("%d\n",circle->data);
    while(bl!=circle){             //遍历
        printf("%d\n",bl->data);
        bl=bl->next;
    }

}

```
