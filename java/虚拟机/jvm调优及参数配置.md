##JVM����   �� -Xmx10240m -Xms10240m -Xmn5120m -XXSurvivorRatio=3  -Xss128k

* 1. -Xmx�����Ѵ�С
* 2. -Xms����ʼ�Ѵ�С
* 3. -Xmn���������С
* 4. -XXSurvivorRatio���������Eden����Survivor���Ĵ�С��ֵ
* 5. -Xss��ÿ���̵߳Ķ�ջ��С

``` html
�����5120m�� Eden : Survivor=3��Survivor����С=1024m��Survivor���������������������Ϊ5�ݣ�ÿ��Survivor��ռһ�ݣ����ܴ�СΪ2048m��

-Xms��ʼ�Ѵ�С����С�ڴ�ֵΪ10240m

![Image text](https://github.com/yinyinfeiqiao/advanced-java-skills/blob/master/photo/20181222111036133.jpg)

```
