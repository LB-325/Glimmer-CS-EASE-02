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
    if(h==NULL){
    printf("内存分配失败\n");
    return NULL;
}
    h->data=1;
    h->next=h;
    return h;
}


li* getl(li *l){    //得到尾节点地址
    li *p=l;
    while(p->next!=l){
        p=p->next;
    }
    return p;
}

void H(li **l,in e){       //头插法，在头数据后插入一个新数据，*l是第一个节点，e是插入的数据元素
    li *p=(li*)malloc(sizeof(li));
    if(p==NULL){
    printf("内存分配失败\n");
    return;
}
    p->data=e;
    p->next=*l;
    li *t=getl(*l);
    t->next=p;
    *l=p;
}



li* T(li *l,in e){     //尾插法，在链表最后插入数据
    li *tail;
    li *o=l;
    tail=getl(o);
    li *p=(li*)malloc(sizeof(li));
    if(p==NULL){
    printf("内存分配失败\n");
    return NULL;
}
    p->data=e;
    p->next=tail->next;
    tail->next=p;
    return p;
}

void list(li *l){        //遍历，将链表中数据全部输出一次
    li *p=l;
    printf("%d\n",p->data);
    p=p->next;
    while(p!=l){
        printf("%d\n",p->data);
        p=p->next;
    }
    printf("\n");
}

int D(li **l,int LOCATION){     //删除数据，删除第LOCATION个节点数据
    li *p=*l;
    int i=1;
    while(i<LOCATION-1){
        p=p->next;
        i++;
        if(p==*l){
            return 0;
        }
    }

    if(LOCATION<1){
        printf("所删除的位置信息错误\n");
        return 0;
    }
    if(i==1){
        li *t=getl(*l);
        t->next=p->next;
        *l=p->next;
        free(p);
        return 0;
    }
    li *q;
    q=p->next;
    p->next=q->next;
    free(q);      //释放内存
}

int length(li *l){       //测长度
    int i;
    li *k=l;
    for(i=1;k->next!=l;i++){
        k=k->next;
    }
    return i;

}



int main(){
    li *circle=init();
    T(circle,1);            //输入得到part1中环形链表
    T(circle,1);
    T(circle,1);
    H(&circle,3);
    H(&circle,2);
    H(&circle,1);
    T(circle,1);
    T(circle,3);
    T(circle,1);
    D(&circle,9);
    H(&circle,1);
    H(&circle,2);
    H(&circle,1);
    T(circle,2);
    T(circle,2);
    T(circle,2);
    H(&circle,2);
    H(&circle,1);
    H(&circle,2);
    D(&circle,1);
    H(&circle,2);
    H(&circle,2);
    H(&circle,1);
    T(circle,1);
    T(circle,2);
    T(circle,2);
    D(&circle,23);
    T(circle,2);
    T(circle,1);
    T(circle,1);
    T(circle,2);
    T(circle,2);
    T(circle,2);
    H(&circle,1);
    H(&circle,2);
    H(&circle,1);
    H(&circle,1);
    H(&circle,1);
    H(&circle,1);

    int a,b,c,m,n,i,len;
    len=length(circle);      //得出总长度len
    li *k=circle;
    for(i=1;k->data!=3;i++){      //得出3节点所在位置i
        k=k->next;
    }

    li *k0=k;
    for(m=1;len>0;m++){
        if(m<len){
        n=1;
        while(n<m){       //找到第m轮第m个
            n++;
            k=k->next;
            i++;
        }
        if(i>len){          //控制i不超过总长度，i表示要删除的第m轮第m个节点在链表中的位置（第i个）
            i=i-len;
        }
        printf("%d",k->data);
        k=k->next;
        k0=k;
        D(&circle,i);
        len--;
        }
           else{
            a=m%len;
            if(a==0){
                a=len;
            }
            n=1;
            while(n<a){       //找到第m轮第m个
              n++;
              k=k->next;
              i++;
            }
            if(i>len){          //控制i不超过总长度，i表示要删除的第m轮第m个节点在链表中的位置（第i个）
              i=i-len;
            }
            printf("%d",k->data);
            k=k->next;
            k0=k;
            D(&circle,i);
            len--;
           } 
    }

}


```

---

输出结果：3112111122212122121212111211112221
