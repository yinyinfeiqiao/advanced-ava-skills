�̵�Zookeeper�ڷֲ�ʽ�ܹ��е�Ӧ��

�����˽⵽ Kafka ���������ش���£����ܻ��ṩ�Թ����Ԫ�����ٲû����������� Zookeeper ����������������Ҳ�൱ǿ�ҡ���ôһ����� Zookeeper �ڷֲ�ʽϵͳ�а���ʲô��ɫ��Ŀǰ Zookeeper ��Ӧ������Щ�ֲ�ʽ�ܹ��У����Ĵ� Zookeeper ���������̵���Щ�벻�� Zookeeper �ķֲ�ʽ�����ܹ���

  

һ. Zookeeper ����

  

Zookeeper ��һ�������ܡ��߿ɿ��ķֲ�ʽЭ��ϵͳ���� Google Chubby ��һ����Դʵ�֡�Zookeeper �ܹ�Ϊ�ֲ�ʽӦ���ṩһ���Է����ṩ�Ĺ��ܰ���������ά�����������񡢷ֲ�ʽͬ���������ȡ�  

Zookeeper ʹ�� Zab Э�鴫�� leader ��״̬�ı䣬��֤ leader �� follower ��һ���ԡ�Zab ȫ�� Zookeeper Atomic Broadcast protocol���� Paxos ��ʶ�㷨�ľ���ʵ�֡�

Zookeeper?Ӧ�÷ǳ��㷺��Ӧ�ó�����Ҫ������

*   ���ݷ������ģ��������ģ�
    
*   �������񣨱���ȫ��ΨһID��
    
*   �ֲ�ʽЭ������Watcher���첽֪ͨ��
    
*   ������⣨��ʱ�ڵ㣩
    
*   ��������ϱ�����ʱ�ڵ㣩
    
*   Masterѡ�٣���ʱ�ڵ㡢Watcher��
    
*   �ֲ�ʽ������ʱ�ڵ㡢Watcher��
    

ǰ�����˵ Zookeeper ��һ�������ܡ��߿ɿ���ϵͳ��֮�����Ǹ�������Ҫ��Ϊ Zookeeper �������ڴ��У����� Zookeeper ͨ���Ǽ�Ⱥģʽ�������ڵ�����ϼ���֤����ɿ��ԡ�

��. Kafka �� Zookeeper

  

Zookeeper �� Kafka �ܹ��а�������Ҫ��ɫ��Kafka ʹ�� Zookeeper ����Ԫ���ݹ������� broker ע�����Ϣ������ Topic��Partition ��Ϣ�ȣ�ѡ�� Partition Leader���Ͱ汾 Kafka Consumer �� offset ��ϢҲ������ Zookeeper �С�  

���Ǵ� Kafka �ܹ������� Kafka �� Zookeeper �Ĺ�ϵ ������

��Դ����������

��ͼ����ʾ��Kafka Producer ��ֱ������ broker.list �б���Broker ����ʹ�� Zookeeper ע�� broker ��Ϣ����� Partition leader ����ԣ�Comsumer ����ʹ�� Zookeeper ע�� comsumer ��Ϣ��ͬʱ�������� broker �б����� Partition leader ���� socket ���ӻ�ȡ��Ϣ��

  

��. Hadoop?��?Zookeeper

  

Zookeeper ����Ϊ Hadoop ����Ŀ��չ�����ģ���������Ŀ�����Ϊ Hadoop ��̬���֮���ṩһ����Э������ģ������ Hadoop ��ϵ��������Ҫָ HDFS �� YARN����ʹ�ù㷺��  

�� Hadoop �У�Zookeeper ��Ҫ����ʵ�� HA��High Availability�������� HDFS NameNode �� YARN ResourceManager �� HA������� YARN ResourceManager �� HA �ܹ�����������

��Դ��Hadoop����

����ͼ��ʾ�������ʵ��ϸ�����ﲻ��׸���ˣ�HDFS ���� Zookeeper ʵ�� NameNode ?HA ��ԭ��ͬ�ϡ�

��. HBase �� Zookeeper

  

HBase �Ǵ���������ʹ����㷺�� NoSQL ���ݿ⣬Zookeeper �� HBase �ܹ���ͬ����������Ҫ��ɫ��������������һ�� HBase �ļܹ�ͼ��  

��Դ��MAPR����

������ʾ��HBase ��Ҫ���� HMaster��RegionServer��Zookeeper ���ֽ�ɫ�����ǿ��Ժ�����Ŀ�����HBase ʹ�� Zookeeper ��Ϊ�ֲ�ʽЭ��������ά����Ⱥ�з����״̬�����е� RegionServer �� Active HMaster ��Ҫ�� Zookeeper ���ֻỰ��session����Zookeeper ά������Щ servers �ǽ������õģ������� server ����ʱ����֪ͨ��

��. Solr �� Zookeeper

  

Zookeeper �� Solr �ļܹ���Ҳ�зǳ���Ҫ��Ӧ�á���������������ͨ��ʹ�� SolrCloud ģʽ��Solr ��Ⱥ���� Zookeeper �������������Ϣ�ͼ�Ⱥ������״̬����ʹ�� Zookeeper �������ڵ�ѡ�١�

�ἰ Solr �Ͳ��ò�˵˵ Elasticsearch��Elasticsearch ͬ Solr һ��Ҳ�Ƿǳ����е��������棬���� Elasticsearch ȴ������ Zookeeper ���ֲ�ʽЭ���������Դ���Ⱥ�ֲ�ʽЭ��ϵͳ��Zen Discovery �� Zen2������Ҳ�� Elasticsearch �� Solr ֮�����Ҫ����֮һ��

��. д�����

  

����֪�� Zookeeper �ڷֲ�ʽϵͳ�ܹ���ʹ�ù㷺�������ص������ Zookeeper �ڴ���������ֲ�ʽ�ܹ��еļ�������Ӧ�ã�����֮�⣬Zookeeper ���и����ʹ�ó����������� Spring Cloud ΢����ܹ���Dubbo �ֲ�ʽ�ܹ��ж���Ӧ�ã�����Ͳ���׸���ˡ�

  

�ο���

*   Zookeeperԭ������Hadoop��HBase�е�Ӧ�ã�https://www.cnblogs.com/iyulang/p/6604914.html
    
*   kafka��zookeeper֮��Ĺ�����https://yq.aliyun.com/articles/653930
    
*   zookeeper�ڴ��ͷֲ�ʽϵͳ�е�Ӧ�ã�https://www.cnblogs.com/aoshicangqiong/p/7978418.html
    