# Data Structure——Linear List

## 线性表

### 顺序表

> 设a1的储存地址为LOC(a1),每个数据元素占L个存储单元，则第i个数据元素的地址为：LOC(ai) = LOC(a1) + (i-1)L

#### 顺序存储结构

    #define MAXSIZE 100
    typedef struct List
    {
        ElemType data[MAXSIZE];
        int last;
    }SeqList;

    SeqList *L;

> 数组data，用于存放数据元素
>
> 线性表长度：L->Last+1
>
> 存储空间：L->data[0]--L->data[L->Last]

#### 初始化

    void Init(SeqList *L)
    {
        L = (SeqList*)malloc(sizeof(SeqList));
        if(L==NULL)
            return;
        L->last = -1;
    }

#### 按值查找

    int LocateList(SeqList *L, ElemType x)
    {
        int i = 0;
        while(i<=L->last&&x!=L->data[i])
            i++;
        if(i>L->last)
            return 1;
        else
            return i;       //返回储存位置 
    }

#### 插入运算

    int InsertList(SeqList *L, int i, ElemType x)
    {
        int j;
        if(L->last==Maxsize-1)          
        {
            printf("表满");
            return -1； 
        }
        if(i<1||i>L->last+2)
        {
            printf("插入位置错误");
            return -1; 
        }
        for(j=L->last;j>=i-1;j--){          //往后移一位
            L->data[j+1] = L->data[j];  
            L->data[i-1] = x;               
            L->last++;
            return 1;
        }
    }

> 时间复杂度：O(n);

#### 删除操作

    int DeleteList(SeqList *L, int i)
    {
        int j;
        if(i<1||i>L->last+1)
        {
            printf("不存在第i个元素");
            return 0; 
        }
        for(j=i;j<=L->last;j++)
        {
            L->data[j-1] = L->data[j];
            L->last--;
            return 1; 
        }
    }
> 时间复杂度：O(n);

#### A=A∪B

    void Union(SeqList *la, SeqList *lb)
    {
        int i,j,la_len,lb_len;
        ElemType e;
        for(i=0;i<lb->last+1;i++)
        {
            e = lb->data[i];
            j=0;
            while(j<la->last+1 && e!=la->data[j])
                j++;
            if(j>=la->last+1)
                if(la->last<Maxsize - 1)
                    La->data[++(la->last)] = e;
        }
    }
> 时间复杂度：O((la->last+1)*(lb->last+1));

#### 顺序表A&B,其元素有序递增，将之合并为C，有序递增

    void merge(SeqList *A, SeqList *B, SeqList *C)
    {
        int i = 0, j = 0, k = 0;
        while(i<A->last+1 && j<B->last+1)
        {
            if(A->data[i] <= B->data[j])
                C->data[k++] = A->data[i++];
            else
                C->data[k++] = B->data[j++];
        }
        while(i <= A->last)
            C->data[k++] = A->data[i++];
        while(j <= B->last)
            C->data[k++] = A->data[i++];
        C->last = k - 1;
    }

#### 线性表的优点

- 逻辑相邻的元素存储的物理位置也相邻

- 随机存取表中任意一个元素

#### 线性表的缺点

- 插入和删除时，需要移动大量元素

- 存储需要预先分配空间，表长变化大时，难以确定存储规模

---

### 单链表

> 数据域 + 指针域

#### 单链表存储结构

    typedef struct node
    {
        ElemType data;
        struct node *next;
    }LNode, *LinkList;
    
    LinkList L;

> 带头结点：L->next = NULL;

#### 初始化单链表

    void InitLinkList(LinkList L)
    {
        L = (LinkList)malloc(sizeof(LNode));
        if(L==NULL)
            return;
        L->next = NULL;
        return;
    }

#### 头插法

> 建立一个带头结点的单链表
>
> 将元素逆序插入，不是结束标志，申请结点s插入到头结点之后

    void CreateFromHead(LinkList L)
    {
        LinkList s;
        char c;
        int flag = 1;
        L = (LinkList)malloc(sizeof(LNode));
        L->next = NULL;
        while(flag)
        {
            c = getchar();
            if(c!='$')
            {
                s = (LinkList)malloc(sizeof(LNode));
                s->data = c;
                s->next = L->next;
                L->next = s;
            }
            else
            {
                flag = 0;
            }
        }
    }

#### 尾插法

> 建立一个带头结点的单链表,设一个指针r指向表尾L
>
> 不是结束标志，申请结点s，将s插入到r所指的结点的后面，然后r指向新的表尾结点s

    void CreateFromTail(LinkList L)
    {
        LinkList s,r;
        L = (LinkList)malloc(sizeof(LNode));
        L->next = NULL;                         //创建头结点
        r = L;                                  //r指向L
        char c;
        int flag = 1;
        while(flag)
        {
            c = getchar();
            if(c!='$')
            {
                s = (LinkList)malloc(sizeof(LNode));
                s->data = c;
                r->next = s;
                r=s;
            }
            else
            {
                flag = 0;
                r->next = NULL;
            }
        }
    }

#### 求单链表长度

> 设一个临时变量p指向头结点，计数器j等于0
>
> 当p->next!=NULL,循环：指针p后移，计数器加一

    int ListLength(LinkList L)
    {
        LinkList p;
        p = L;
        int j = 0;
        while(p->next!=NULL){
            p = p->next;
            j++;
        }
        return j;
    }

#### 按序号查找(找第i个元素)

    int LocateList(LinkList L, int i)
    {
        LinkList p = L;
        int j = 0;
        while(p->next!=NULL && j<i)
        {
            p = p->next;
            j++;
        }
        if(i==j)
            return j;
        else
            return -1;
    }

#### 按值查找(x)

    int Locate_List(LinkList L,ElemType x)
    {
        LinkList p = L->next;
        while(p!=NULL && x!=p->data)
        {
            p = p->next;
        }
        if(p)
            return -1;
        else
            return 1;
    }

#### 单链表的插入操作

> 寻找第i-1个结点

    int InsertList(LinkList L, int i, char x)
    {
        LinkList p,s;
        p = L;
        int k = 0;
        while(p && k<i-1)     //找第i-1个结点
        {
            p = p->next;
            k++;
        }
        if(k!=i-1)
        {
            printf("插入位置不合理");
            return -1;
        }
        s = (LinkList)malloc(sizeof(LNode));
        s->data = x;
        s->next = p->next;
        p->next = s;
        return 1;
    }

#### 单链表的删除

> 寻找第i-1个结点
>
> 用r指针指向第i个结点(要删除的)
>
> 断开连接，free(r)

    int DeleteList(LinkList L, int i, char *x)
    {
        LinkList p = L;
        LinkList r;
        int k = 0;
        while(p->next && k<i-1)
        {
            p = p->next;
            k++;
        }
        if(k!=i-1)
        {
            printf("删除位置不合理");
            return -1;
        }
        r = p->next;            //用r指针指向第要删除的结点
        p->next = r->next;
        *x = r->data;
        free(r);
        return 1;
    }

#### 单链表总结

- 在单链表上插入，删除一个结点，必须知道其前驱结点

- 单链表不具有按序号随机访问的特点，插入位置只能从头指针开始一个一个顺序进行

### 循环单链表

> 假设p指向链表的最后一个节点时判不为空：L->next != L为真

#### 将两个带头结点的循环单链表La，Lb合并

> 找到链表尾结点，并由指针指向尾结点
>
> 将第一个链表的尾结点与第二个结点的第一个结点连接起来
>
> 修改第二个表的尾指针，指向第一个表的头结点

    void merge_1(LinkList La, LinkList Lb)
    {
        LinkList p,q;
        q = La;
        p = Lb;
        while(p->next!=La)
            p = p->next;
        while(q->next!=Lb)
            q = q->next;
        q->next = La;
        p->next = Lb->next;
        free(Lb);
    }

#### 用两个尾指针标识的循环链表的连接

> 用指针将r1的头结点记住
>
> 释放r2的头结点

    void merge_2(LinkList r1, LinkList r2)
    {
        LinkList p = r1->next;
        r1->next = r2->next->next;
        free(r2->next);
        r2->next = p;
    }

### 双向链表

#### 双向链表结构定义

    typedef struct DLnode
    {
        ElemType data;
        struct DLnode *prior,*next;
    }DLnode, *DLinkList;

> 寻找任意一个结点的前驱和后继变得方便
>
> p->prior->next = p = p->next->prior

#### 双向链表插入

    int InsertDLinkList(DLinkList L, int i, ElemType)
    {
        DLinkList s,p;
        p = L;
        int k = 0;
        while(p && k<i)     //找第i个结点
        {
            p = p->next;
            k++;
        }
        if(k!=i)
        {
            printf("插入位置不合理");
            return -1;
        }
        s = (DLinkList)malloc(sizeof(DLnode));
        s->data = e;
        s->prior = p->prior;
        p->prior->next = s;
        s->next = p;
        p->prior = s;
        return 1;
    }

#### 求A-B

    void Difference(LinkList La, LinkList Lb)
    {
        LinkList pre,p,q,r;
        pre = La;
        p = La->next;
        while(p)
        {
            q = Lb->next;
            while(q && q->data!=p->data)
            {
                q = q->next;
            }
            if(q)           //b中的元素a中也有
            {
                r = p;
                pre->next = p->next;
                p = p->next;
                free(r);
            }
            else
            {
                pre = p;
                p = p->next;
            }
        }
    }

### 顺序表和链表比较

- 顺序表

> 优点：
>
> 省内存，可随机访问
>
> 缺点：
>
> 插入删除时需移动大量元素，需预先分配空间

- 链表

> 优点：
>
> 插入删除不需要移动元素，修改指针即可
>
> 缺点：
>
> 内存利用率低

- 总结

> 需要大量元素插入删除时用链表
>
> 按照实际情况选

---
