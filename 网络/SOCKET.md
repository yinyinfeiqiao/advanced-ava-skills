<!-- GFM-TOC -->
* [һ��I/O ģ��](#һio-ģ��)
    * [����ʽ I/O](#����ʽ-io)
    * [������ʽ I/O](#������ʽ-io)
    * [I/O ����](#io-����)
    * [�ź����� I/O](#�ź�����-io)
    * [�첽 I/O](#�첽-io)
    * [��� I/O ģ�ͱȽ�](#���-io-ģ�ͱȽ�)
* [����I/O ����](#��io-����)
    * [select](#select)
    * [poll](#poll)
    * [�Ƚ�](#�Ƚ�)
    * [epoll](#epoll)
    * [����ģʽ](#����ģʽ)
    * [Ӧ�ó���](#Ӧ�ó���)
* [�ο�����](#�ο�����)
<!-- GFM-TOC -->


# һ��I/O ģ��

һ���������ͨ�����������׶Σ�

- �ȴ�����׼����
- ���ں�����̸�������

����һ���׽����ϵ������������һ��ͨ���漰�ȴ����ݴ������е�������ȴ����ݵ���ʱ���������Ƶ��ں��е�ĳ�����������ڶ������ǰ����ݴ��ں˻��������Ƶ�Ӧ�ý��̻�������

Unix ������ I/O ģ�ͣ�

- ����ʽ I/O
- ������ʽ I/O
- I/O ���ã�select �� poll��
- �ź�����ʽ I/O��SIGIO��
- �첽 I/O��AIO��

## ����ʽ I/O

Ӧ�ý��̱�������ֱ�����ݴ��ں˻��������Ƶ�Ӧ�ý��̻������вŷ��ء�

Ӧ��ע�⵽���������Ĺ����У�����Ӧ�ý��̻�����ִ�У������������ζ����������ϵͳ������������Ϊ����Ӧ�ý��̻�����ִ�У����Բ����� CPU ʱ�䣬����ģ�͵� CPU �����ʻ�Ƚϸߡ�

��ͼ�У�recvfrom() ���ڽ��� Socket ���������ݣ������Ƶ�Ӧ�ý��̵Ļ����� buf �С������ recvfrom() ����ϵͳ���á�

```c
ssize_t recvfrom(int sockfd, void *buf, size_t len, int flags, struct sockaddr *src_addr, socklen_t *addrlen);
```

<div align="center"> <img src="pics/1492928416812_4.png"/> </div><br>

## ������ʽ I/O

Ӧ�ý���ִ��ϵͳ����֮���ں˷���һ�������롣Ӧ�ý��̿��Լ���ִ�У�������Ҫ���ϵ�ִ��ϵͳ��������֪ I/O �Ƿ���ɣ����ַ�ʽ��Ϊ��ѯ��polling����

���� CPU Ҫ��������ϵͳ���ã��������ģ�͵� CPU �����ʱȽϵ͡�

<div align="center"> <img src="pics/1492929000361_5.png"/> </div><br>

## I/O ����

ʹ�� select ���� poll �ȴ����ݣ����ҿ��Եȴ�����׽����е��κ�һ����Ϊ�ɶ�����һ���̻ᱻ��������ĳһ���׽��ֿɶ�ʱ���أ�֮����ʹ�� recvfrom �����ݴ��ں˸��Ƶ������С�

�������õ������̾��д����� I/O �¼����������ֱ���Ϊ Event Driven I/O�����¼����� I/O��

���һ�� Web ������û�� I/O ���ã���ôÿһ�� Socket ���Ӷ���Ҫ����һ���߳�ȥ�������ͬʱ�м�������ӣ���ô����Ҫ������ͬ�������̡߳�����ڶ���̺Ͷ��̼߳�����I/O ���ò���Ҫ�����̴߳������л��Ŀ�����ϵͳ������С��

<div align="center"> <img src="pics/1492929444818_6.png"/> </div><br>

## �ź����� I/O

Ӧ�ý���ʹ�� sigaction ϵͳ���ã��ں��������أ�Ӧ�ý��̿��Լ���ִ�У�Ҳ����˵�ȴ����ݽ׶�Ӧ�ý����Ƿ������ġ��ں������ݵ���ʱ��Ӧ�ý��̷��� SIGIO �źţ�Ӧ�ý����յ�֮�����źŴ�������е��� recvfrom �����ݴ��ں˸��Ƶ�Ӧ�ý����С�

����ڷ�����ʽ I/O ����ѯ��ʽ���ź����� I/O �� CPU �����ʸ��ߡ�

<div align="center"> <img src="pics/1492929553651_7.png"/> </div><br>

## �첽 I/O

Ӧ�ý���ִ�� aio_read ϵͳ���û��������أ�Ӧ�ý��̿��Լ���ִ�У����ᱻ�������ں˻������в������֮����Ӧ�ý��̷����źš�

�첽 I/O ���ź����� I/O ���������ڣ��첽 I/O ���ź���֪ͨӦ�ý��� I/O ��ɣ����ź����� I/O ���ź���֪ͨӦ�ý��̿��Կ�ʼ I/O��

<div align="center"> <img src="pics/1492930243286_8.png"/> </div><br>

## ��� I/O ģ�ͱȽ�

- ͬ�� I/O�������ݴ��ں˻��������Ƶ�Ӧ�ý��̻������Ľ׶Σ��ڶ��׶Σ���Ӧ�ý��̻�������
- �첽 I/O���ڶ��׶�Ӧ�ý��̲���������

ͬ�� I/O ��������ʽ I/O��������ʽ I/O��I/O ���ú��ź����� I/O �����ǵ���Ҫ�����ڵ�һ���׶Ρ�

������ʽ I/O ���ź����� I/O ���첽 I/O �ڵ�һ�׶β���������

<div align="center"> <img src="pics/1492928105791_3.png"/> </div><br>

# ����I/O ����

select/poll/epoll ���� I/O ��·���õľ���ʵ�֣�select ���ֵ����磬֮���� poll������ epoll��

## select

```c
int select(int n, fd_set *readfds, fd_set *writefds, fd_set *exceptfds, struct timeval *timeout);
```

select ����Ӧ�ó������һ���ļ����������ȴ�һ�����߶����������Ϊ����״̬���Ӷ���� I/O ������

- fd_set ʹ������ʵ�֣������Сʹ�� FD_SETSIZE ���壬����ֻ�ܼ������� FD_SETSIZE �����������������������͵����������ͣ�readset��writeset��exceptset���ֱ��Ӧ����д���쳣���������������ϡ�

- timeout Ϊ��ʱ���������� select ��һֱ����ֱ�������������¼�������ߵȴ���ʱ�䳬�� timeout��

- �ɹ����÷��ؽ������ 0�������ؽ��Ϊ -1����ʱ���ؽ��Ϊ 0��

```c
fd_set fd_in, fd_out;
struct timeval tv;

// Reset the sets
FD_ZERO( &fd_in );
FD_ZERO( &fd_out );

// Monitor sock1 for input events
FD_SET( sock1, &fd_in );

// Monitor sock2 for output events
FD_SET( sock2, &fd_out );

// Find out which socket has the largest numeric value as select requires it
int largest_sock = sock1 > sock2 ? sock1 : sock2;

// Wait up to 10 seconds
tv.tv_sec = 10;
tv.tv_usec = 0;

// Call the select
int ret = select( largest_sock + 1, &fd_in, &fd_out, NULL, &tv );

// Check if select actually succeed
if ( ret == -1 )
    // report error and abort
else if ( ret == 0 )
    // timeout; no event detected
else
{
    if ( FD_ISSET( sock1, &fd_in ) )
        // input event on sock1

    if ( FD_ISSET( sock2, &fd_out ) )
        // output event on sock2
}
```

## poll

```c
int poll(struct pollfd *fds, unsigned int nfds, int timeout);
```

poll �Ĺ����� select ���ƣ�Ҳ�ǵȴ�һ���������е�һ����Ϊ����״̬��

poll �е��������� pollfd ���͵����飬pollfd �Ķ������£�

```c
struct pollfd {
               int   fd;         /* file descriptor */
               short events;     /* requested events */
               short revents;    /* returned events */
           };
```


```c
// The structure for two events
struct pollfd fds[2];

// Monitor sock1 for input
fds[0].fd = sock1;
fds[0].events = POLLIN;

// Monitor sock2 for output
fds[1].fd = sock2;
fds[1].events = POLLOUT;

// Wait 10 seconds
int ret = poll( &fds, 2, 10000 );
// Check if poll actually succeed
if ( ret == -1 )
    // report error and abort
else if ( ret == 0 )
    // timeout; no event detected
else
{
    // If we detect the event, zero it out so we can reuse the structure
    if ( fds[0].revents & POLLIN )
        fds[0].revents = 0;
        // input event on sock1

    if ( fds[1].revents & POLLOUT )
        fds[1].revents = 0;
        // output event on sock2
}
```

## �Ƚ�

### 1. ����

select �� poll �Ĺ��ܻ�����ͬ��������һЩʵ��ϸ����������ͬ��

- select ���޸����������� poll ���᣻
- select ������������ʹ������ʵ�֣�FD_SETSIZE ��СĬ��Ϊ 1024�����Ĭ��ֻ�ܼ��� 1024 �������������Ҫ���������������Ļ�����Ҫ�޸� FD_SETSIZE ֮�����±��룻�� poll û�����������������ƣ�
- poll �ṩ�˸�����¼����ͣ����Ҷ����������ظ������ϱ� select �ߡ�
- ���һ���̶߳�ĳ�������������� select ���� poll����һ���̹߳ر��˸����������ᵼ�µ��ý����ȷ����

### 2. �ٶ�

select �� poll �ٶȶ��Ƚ�����ÿ�ε��ö���Ҫ��ȫ����������Ӧ�ý��̻��������Ƶ��ں˻�������

### 3. ����ֲ��

�������е�ϵͳ��֧�� select������ֻ�бȽ��µ�ϵͳ֧�� poll��

## epoll

```c
int epoll_create(int size);
int epoll_ctl(int epfd, int op, int fd, struct epoll_event *event)��
int epoll_wait(int epfd, struct epoll_event * events, int maxevents, int timeout);
```

epoll_ctl() �������ں�ע���µ������������Ǹı�ĳ���ļ���������״̬����ע������������ں��лᱻά����һ�ú�����ϣ�ͨ���ص������ں˻Ὣ I/O ׼���õ����������뵽һ�������й������̵��� epoll_wait() ����Եõ��¼���ɵ���������

��������������Կ�����epoll ֻ��Ҫ���������ӽ��̻��������ں˻���������һ�Σ����ҽ��̲���Ҫͨ����ѯ������¼���ɵ���������

epoll �������� Linux OS��

epoll �� select �� poll ����������û���������������ơ�

epoll �Զ��̱߳�̸����Ѻã�һ���̵߳����� epoll_wait() ��һ���̹߳ر���ͬһ��������Ҳ��������� select �� poll �Ĳ�ȷ�������

```c
// Create the epoll descriptor. Only one is needed per app, and is used to monitor all sockets.
// The function argument is ignored (it was not before, but now it is), so put your favorite number here
int pollingfd = epoll_create( 0xCAFE );

if ( pollingfd < 0 )
 // report error

// Initialize the epoll structure in case more members are added in future
struct epoll_event ev = { 0 };

// Associate the connection class instance with the event. You can associate anything
// you want, epoll does not use this information. We store a connection class pointer, pConnection1
ev.data.ptr = pConnection1;

// Monitor for input, and do not automatically rearm the descriptor after the event
ev.events = EPOLLIN | EPOLLONESHOT;
// Add the descriptor into the monitoring list. We can do it even if another thread is
// waiting in epoll_wait - the descriptor will be properly added
if ( epoll_ctl( epollfd, EPOLL_CTL_ADD, pConnection1->getSocket(), &ev ) != 0 )
    // report error

// Wait for up to 20 events (assuming we have added maybe 200 sockets before that it may happen)
struct epoll_event pevents[ 20 ];

// Wait for 10 seconds, and retrieve less than 20 epoll_event and store them into epoll_event array
int ready = epoll_wait( pollingfd, pevents, 20, 10000 );
// Check if epoll actually succeed
if ( ret == -1 )
    // report error and abort
else if ( ret == 0 )
    // timeout; no event detected
else
{
    // Check if any events detected
    for ( int i = 0; i < ret; i++ )
    {
        if ( pevents[i].events & EPOLLIN )
        {
            // Get back our connection pointer
            Connection * c = (Connection*) pevents[i].data.ptr;
            c->handleReadEvent();
         }
    }
}
```


## ����ģʽ

epoll ���������¼������ִ���ģʽ��LT��level trigger���� ET��edge trigger����

### 1. LT ģʽ

�� epoll_wait() ��⵽�������¼�����ʱ�������¼�֪ͨ���̣����̿��Բ�����������¼����´ε��� epoll_wait() ���ٴ�֪ͨ���̡���Ĭ�ϵ�һ��ģʽ������ͬʱ֧�� Blocking �� No-Blocking��

### 2. ET ģʽ

�� LT ģʽ��ͬ���ǣ�֪֮ͨ����̱������������¼����´��ٵ��� epoll_wait() ʱ�����ٵõ��¼������֪ͨ��

�ܴ�̶��ϼ����� epoll �¼����ظ������Ĵ��������Ч��Ҫ�� LT ģʽ�ߡ�ֻ֧�� No-Blocking���Ա�������һ���ļ������������/����д�����Ѵ������ļ������������������

## Ӧ�ó���

�����ײ���һ�ִ����ΪֻҪ�� epoll �Ϳ����ˣ�select �� poll ���Ѿ���ʱ�ˣ���ʵ���Ƕ��и��Ե�ʹ�ó�����

### 1. select Ӧ�ó���

select �� timeout ��������Ϊ 1ns���� poll �� epoll Ϊ 1ms����� select ����������ʵʱ��Ҫ��Ƚϸߵĳ���������˷�Ӧ�ѵĿ��ơ�

select ����ֲ�Ը��ã���������������ƽ̨��֧�֡�

### 2. poll Ӧ�ó���

poll û��������������������ƣ����ƽ̨֧�ֲ��Ҷ�ʵʱ��Ҫ�󲻸ߣ�Ӧ��ʹ�� poll ������ select��

### 3. epoll Ӧ�ó���

ֻ��Ҫ������ Linux ƽ̨�ϣ��д�������������Ҫͬʱ��ѯ��������Щ��������ǳ����ӡ�

��Ҫͬʱ���С�� 1000 ������������û�б�Ҫʹ�� epoll����Ϊ���Ӧ�ó����²��������� epoll �����ơ�

��Ҫ��ص�������״̬�仯�࣬���Ҷ��Ƿǳ����ݵģ�Ҳû�б�Ҫʹ�� epoll����Ϊ epoll �е��������������洢���ں��У����ÿ����Ҫ����������״̬�ı䶼��Ҫͨ�� epoll_ctl() ����ϵͳ���ã�Ƶ��ϵͳ���ý���Ч�ʡ����� epoll ���������洢���ںˣ������׵��ԡ�
