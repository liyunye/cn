# 跨区域复制设置

跨区域复制（Bucket Cross-Region Replication） 是跨不同区域的Bucket自动、异步复制Object，它会将对源Bucket中的对象的改动（除删除操作）同步到目标Bucket。跨区域复制功能能够很好的满足用户数据复制或者提供Bucket跨区域容灾的需求。目标Bucket中的对象是源Bucket中对象的精确副本，它们具有相同的对象名、元数据以及内容。

## 使用场景

当您有以下需要时，设置跨区域复制可能对您有所帮助： 

* 数据复制：由于业务原因，需要将数据从一个存储区域迁移至另一个存储区域，原空间数据仍会保留。

* 合规性要求：合规性要求所规定的数据需要跨一定距离保存一份副本。通过跨区域同步管理功能，可以在远距离的存储区域之间同步数据以满足这些合规性要求。

* 数据备份与容灾：如果您对所有写入的数据都希望在异地存储区域维护一份副本，以备发生如海啸、地震等特大灾难导致存储区域损毁时，还能启用异地存储区域的备份数据。

* 最大限度减少延迟：客户处于两个地理位置。为了最大限度缩短访问对象时的延迟，可以在地理位置与用户较近的存储区域维护对象副本。


## 在控制台中设置过程如下：


1.登入控制台->对象存储->空间管理->进入某个Bucket->空间设置->跨区域复制

![跨区域复制](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-041.png)

2.单击 开启按钮，打开跨区域复制规则配置对话框。

![配置跨区域复制](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-042.png)

3.选择目标存储空间所在的地域及存储空间名称。

细节说明：

* 数据同步的两个存储空间必须分属为两个地域，同地域的存储空间之间不能进行数据同步。

* 开启跨区域同步的两个存储空间都不能同时与其他任何存储空间存在互相同步的关系。

4.选择同步对象。

* 全部文件进行同步：将源存储空间内所有的文件同步到目标存储空间。

* 指定文件名前缀进行同步：将源存储空间内指定前缀的文件同步到目标存储空间。

   a.  您最多可以添加1000个前缀。每条前缀最多1024字节。

   b.  文件前缀不支持重叠前缀，例如text与test/01是不容许的。

5.是否更改存储类型。

 * 勾选更改存储类型：可以更改复制文件存储类型，支持标准存储、低频存储、归档存储和低冗余存储（不推荐）。


6.点击 确认按钮,保存设置。

细节说明：

 * 规则配置完成以后，存储空间同步任务将自动异步进行。数据复制到目标存储空间需要的时间取决于数据的大小，通常几秒钟到几小时不等。

 * 由于开启跨区域复制的源Bucket与目标Bucket均可独立操作，若源Bucket 中新增文件与目标Bucket中文件同名，将覆盖目标Bucket中的同名文件，请谨慎操作。

 * 若存在区域复制规则，源Bucket与目标Bucket均不可删除，必须先关闭跨区域复制。

 * 开启跨区域同步的条件是同步的两个Bucket没有开启与其他Bucket的同步配置，同时不能被其他Bucket同步。举例来说，若 Bucket A 开启了到 Bucket B 的同步，那么您就不能再为 Bucket A 开启到 Bucket C 的同步，除非将 Bucket A到Bucket B 的同步配置修改为到Bucket C。同理，若 Bucket A 开启了到 Bucket B 的同步，这时候再开启 Bucket C 到 Bucket B 的同步也是不允许的。

* 跨区域复制暂不支持历史数据同步。
